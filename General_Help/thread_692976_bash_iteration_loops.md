---
title: "bash iteration loops"
date: 2008-02-10
forum: General Help
---

### Post by mfaust731 on 2008-02-10
k, i need a script that will make a list of files in a given directory, then run a command on each of those files.

I have 
ls *.mpg > mylist                ( which creates the list )

how do a take that list and run my commands on each file?

---

### Post by paultag on 2008-02-10
not sure what you want here, can you give me an example of what its supposed to do?

---

### Post by cknight on 2008-02-13
The find command is probably a better choice here as it can execute for you.  E.g.
```
find . -maxdepth 1 -type f -name "*.png" -exec ls {} \;
```
'find' is the shell command to find files
'.' means search from the current directory
-maxdepth 1 specifies this directory only.  If you leave this out it will search sub directories too
-type f means search for files only
-name "*.png" means search for files ending in .png
-exec specifies that the following action should be executed on each result.  
ls is the action to perform (in this case is just echoes the file name)
{} is replace dynamically with the output of the 'find'
\; is required(?) by bash to end the command

change -exec to -ok to be prompted to perform the specified action on each file.
change ls to rm if, for example, you want to delete each of the matches

---

