---
title: "Pattern matching mass deletion of files"
date: 2007-12-29
forum: General Help
---

### Post by hebetude on 2007-12-29
I'm trying to clean up my mp3 collection.  I want to twiddle it down to just full albums I have.  Anybody know a good SAFE way to delete all directories with less than 5 files in them.  I tried to search for related discussions on this topic but did not get too far.

---

### Post by ghostdog74 on 2007-12-29
this pieces of code finds the number of files in directories
```

# find /yourpath -type d | while read line; 
        do   
             ls "$line" | wc -l
        done   

```
I leave you to do the rest of calculating and comparing against 5 files using if/else or switch etc..

---

### Post by hebetude on 2007-12-29
thanks! I didn't know line existed

---

### Post by ghostdog74 on 2007-12-29
> **hebetude said:**
> thanks! I didn't know line existed

no...line is  just a variable to be defined when each line of the file is passed to the while loop.. you can call it anything you want.

---

### Post by hebetude on 2007-12-29
oh okay, so I guess following a pipe with 'while' lets you do a command per line sent to the pipe?  something like this:
find . -type d | find -type f | wc -l

just sends out a compiled list of all the files in all the directories rather than organized per directory

---

### Post by ghostdog74 on 2007-12-29
> **hebetude said:**
> oh okay, so I guess following a pipe with 'while' lets you do a command per line sent to the pipe?  something like this:
find . -type d | find -type f | wc -l

just sends out a compiled list of all the files in all the directories rather than organized per directory

you don't have to use find 2 times. In your case, if you want to find both files and directories, then don't use -type. Make sense?

```

find /path | wc -l

```


try that out on the command line and see

---

### Post by hebetude on 2008-01-14
I finally got around to figuring out a way to do this, but it occurred to me that this would not give me what I want.  This method would work great if the directory structure is only 1 deep ie.

dir1 --->file1 file2 file3
dir2 ---->file1 file2 file3 file4 file5

but it isnt intelligently checking for files, its just checking for whitespace returned from a ls command.  So it would delete something like this
dir1 ----> subdir1 ---> file1 file2 file3 file4 file5 file6

Because dir1 has only 1 child, it would be flagged for deletion.  Clearly, I need to think this out more to make a mass deletion like this more robust.  The better option was always to remove stuff one by one with some sort of music library tool, deleting relatively empty folders isn't what I really needed to do.

Anways, I learned some stuff about shell scripting!  It was somewhat hard to figure out from the documentation so heres a quick way to check the number of files in each directory.  This is also shows lets you do some logic based on the return from the ls command.

find $1 -type d | while read line;  //find all the directories
        do
          num=$(eval ls "$line" | wc -l)  //store result of ls on a directory
          if test $num -lt 3; then
            //something useful here based on conditional statement
          fi
        done

Thanks for the help in getting here ghostdog

---

