# Quiz questions

This is only a "quiz" in the loosest sense that it's asking questions whose
answers will be part of your grade. Please use *any resources you want*, as
long as you list those resources (e.g. peers, websites, etc.)

## Navigating logs

1. What is the SHA for the last commit made by Prof. Xanda on the branch
xanda_0000_movie_processing?
(For this and future questions, the first 5 characters is plenty - neither
Git nor I need the whole SHA.)
9b257
2. What is the SHA for the last commit associated with line 9 of this file?
b2ed3
3. What did line 12 of this file say in commit d1d83?
"Git nor I need the whole SHA.)"
4. What changed between commit e474c and 82045?
Edits were made to the process_movie_data.py file to change the assignments of gross_sort to lambda x : int(x["Gross"]) instead of lambda x : x["Gross"], and top_five to rows[:-6:-1] instead of rows[:-5:-1].
## Predicting merges

Assume at the start of each of these three questions that your
branch for switching to a top-10 list was called `top_ten`
and your branch generalizing to any number of movies was called `top_N`.
Predict the behavior of these three possible operations - you don't
have to provide a full `diff` but you should describe at a high level
what changes would happen.

These questions are supposed to be separate paths, not cumulative;
for example, you should *not* assume that the operations of 5 were run
before 6. When testing outcomes later in the lab, you should make sure to
revert back to the state of the branch before you started these questions.

5. What do you think would happen if you ran the following commands?
What branches would change, and how?
```
git checkout test
git merge top_N
```
The first command will make test the active branch, or the one that the head pointer points to. 
The second command will take that active test branch and point it to the commit that top_N points to. This enacts the changes made within the top_N branch into the test branch
6. What do you think would happen if you ran the following commands?
What branches would change, and how?
```
git checkout top_ten
git merge test
```
This will make the head pointer point to the top_ten branch, and then top_ten will point to the same commit that test points to, making the changes that were made within the test branch mapped onto the top_ten branch. This procuded a merge conflict error.
7. What do you think would happen if you ran the following commands?
What branches would change, and how?
```
git checkout test
git rebase top_ten
git rebase top_N
```
This will make the head pointer point to the test branch, then append the commits belonging to the top_ten branch to the test branch, then append all of the branches belonging to the top_N branch to the (new version of the) test branch. 