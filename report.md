# Part 1: Edstem Conversation

### Post Title: Practice Skill Demo 3 Bash Script Error

#### Category: Skill Demo
For the bash script in Skill Demo 3 practice, student4's submission is causing a compile error in the terminal, but the terminal then says "Compile successful for submissions/student3", which is not true. In the "results.txt" file under student3's folder, the script also states that the code passed 0 unit tests, but does not say that it had a compile error.

#### Instructor response:
It seems that student3's submission may not have a compile error, or there is an error in the bash script. Can you run the grading script again using "bash grade.sh", and post the entire terminal output?

#### Student response: 
<img width="305" alt="image" src="https://github.com/wangharold001/cse15l-report5/assets/60553459/01132c95-51c1-41a5-888e-9a88fbf0b1fb">

Here is what the terminal is returning while grading student3. It appears that the student didn't import the Scanner class, which explains why the script raised a compile error. However, the script should "echo "$submission_dir: Compile error" > result.txt" by this point, which it doesn't. Here's the if-block in my bash script testing for a compile error: 
##### "if [ $? -e !"0" ]"

#### Instructor response:
It appears that the if-block has a syntax error, by your terminal output. There is another way to test if $? is not equal to 0, but I can't help you beyond there.


### Information about the bug:

For the bash script to be valid in the first place, there needs to be a folder titled "submissions" in the same directory, then subfolders in submissions titled "student1", "student2"...

Each subfolder should contain a .java file titled "Sorter.java" which the grade.sh script will then compile and run as an autograder. Before fixing the bug, every student folder in the submissions directory will have a file called "result.txt" which gives the result of 2 JUnit tests. This is an error, since students whose .java file did not compile should have a message in "result.txt" saying their submission raised a "Compile Error". 

To run the bug, the student should run "bash grade.sh", which will cause the student folders to have the faulty result.txt output. To fix it, the student should edit their bash grade script's if-block from:

###### "if [ $? -e !"0" ]"

to: "if [[ $? -ne 0 ]]".

# Part 2: Reflection

From the past few weeks in lab, I've gotten much more used to the vim command. It's helped me shorten the debugging process a lot since I don't have to use my mouse to click through a maze of folders to access a buggy program; I can instead use vim and edit files directly from the terminal. In addition, the :[line number] command helps me go immediately to where a bug in a program is, as the terminal will often say "error at x line number".


