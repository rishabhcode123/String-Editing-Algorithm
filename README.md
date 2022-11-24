# String-Editing-Algorithm

                     Problem Statement:
                         
                          
                    Implement the string editing algorithm using dynamic programming approach and demonstrate 3 test cases.

                    Applications of String Editing -
                    Spell Checkers, 
                    Spam Filters, 
                    Intrusion Detection System, 
                    Search Engines, 
                    Plagiarism Detection, 
                    Bioinformatics,
                    Digital Forensics 
                    and Information Retrieval Systems

                   CODE -
                   
                   #include <bits/stdc++.h>
                using namespace std;

              int main(){
             string word1= "FIFAWORLDCUP";
             string word2= "FIFAWORLDPUC";


        int n1 = word1.size(), n2 = word2.size();
        vector<vector<int>> dp(n1+1, vector<int>(n2+1, 0));
        
        
        for(int i=0; i<n1+1; i++){
            dp[i][0] = i;
        }
            
        
        for(int j=0; j<n2+1; j++){
            dp[0][j] = j;
        }
            
        for(int i=1; i<n1+1; i++){
            for(int j=1; j<n2+1; j++){
                if(word1[i-1] == word2[j-1])
                    {dp[i][j] = dp[i-1][j-1];}
                else{
                    int insert = dp[i][j-1];
                    int del = dp[i-1][j];
                    int replace = dp[i-1][j-1];
                    
                    dp[i][j] = 1 + min(insert, min(del, replace));
                }
            }
        }
        cout<<"the minimum edits required are "<<dp[n1][n2];
        
}
        
        
Testcase 1 :
        
 An application of string editing for spell correction:

word1= "WORLDCUP"
word2= "WORLDPUC"

Output - the minimum edits required are 2

![Screenshot 2022-11-24 195300](https://user-images.githubusercontent.com/108607292/203808068-35e46405-18e9-4f1e-8995-8553dadc0ceb.png)

Testcase 2 :

word1= "NASHIK"
word2= "NAGPUR"

Output - the minimum edits required are 4


![Screenshot 2022-11-24 195350](https://user-images.githubusercontent.com/108607292/203808263-24cde88a-1fee-4f39-a545-32844656a75f.png)



Testcase 3 -

word1= "SHREYA"
word2= "SURYAA"

Output - the minimum edits required are 3


![Screenshot 2022-11-24 195624](https://user-images.githubusercontent.com/108607292/203808326-9a8aedf3-a1a8-4711-a083-348f9856fa16.png)

Time and Space complexity :


Time Complexity of Recursion - O(min(3^n1, 3^n2)) 
Space Complexity - O(n)    // stack space for recursion

Time Complexity in dynamic prog. -  O(n1 * n2)
Space Complexity - O(n1 * n2)

n1,n2 represents the length of word1 and word2




        
        
        
        
        
        
        
        
        
        
        
        
        
        
        
        
        
        
        
        
        
        
        
     

