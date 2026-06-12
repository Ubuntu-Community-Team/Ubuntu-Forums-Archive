---
title: "rm - cannot remove: No such file or directory"
date: 2015-09-25
forum: General Help
---

### Post by frbastiat on 2015-09-25
I am getting this error when I try to rm two files and have run through many similar forums posts but haven't found a solution. Hopefully I can get this sorted out with a little more direct help! 

I am running Ubuntu 14.04 x86_64 server and this is a list of what I have tried so far(note: all attempts were also made after sudo su):

chmod 777
rm -f file1
wildcards
tab complete
full path rm
ls -i
find . -inum {inum} -exec rm {} ;\
ls -b
ls -q
rm -i -- *

I eliminated one of the files by running mv file1 file2 and it was overwritten so mv works.

---

### Post by rslater on 2015-09-25
Have you checked if the files are append only?  lsattr

---

### Post by frbastiat on 2015-09-25
lsattr file1 returns:
```
lsattr: Function not implemented While reading flags on file1
```

The file is on a drive pool created by FlexRAID. So the filesystem is fuse.FLEXRAIDFS.

---

### Post by nerdtron on 2015-09-25
It would be better for us to understand your situation if you post a screenshot or complete terminal of the error you are having.
First list the file in the current directory, then try to "rm" the files you want to delete. Post the complete screenshot here.

```
ls -lah 
rm [filename]

```

---

### Post by rslater on 2015-09-25
[FONT=Helvetica Neue]"[/FONT][COLOR=#000000]The file is on a drive pool created by FlexRAID. So the filesystem is fuse.  FLEXRAIDFS." 

 Is the file system read only?  Is the[/COLOR][FONT=Helvetica Neue] remote FS where root is no longer root?  Is the file in use or being re-generated such as a database file?[/FONT]

---

### Post by frbastiat on 2015-09-25
.

---

### Post by nerdtron on 2015-09-25
There is probably a special character after the name "file1" probably a space of something.
try using "ls -lbF" to show the non-printing characters.

Or try to remove the file directly with quotes, assuming there is a space after the filename.
```
 rm "file1 "
```

Or use tabbing,
type 
     rm "fil
then tab twice (for autocompletion)
then close with double quotes again "
Hit enter to delete the file.

If all else fails, since you can already ssh on the server, then use Filezilla or WinSCP to connect to the server, then delete the file. Sometimes GUIs are better at handling "filenames with special characters".

---

### Post by nerdtron on 2015-09-25
> **rslater said:**
> [FONT=Helvetica Neue]"[/FONT][COLOR=#000000]The file is on a drive pool created by FlexRAID. So the filesystem is fuse.  FLEXRAIDFS." 

 Is the file system read only?  Is the[/COLOR][FONT=Helvetica Neue] remote FS where root is no longer root?  Is the file in use or being re-generated such as a database file?[/FONT]

It is not filesystem issue. The OP said he was able to move files.
> I eliminated one of the files by running mv file1 file2 and it was overwritten so mv works. 

This is most likely a filename issue. A filename with special characters, which is probably a [space] after the filename.

---

### Post by frbastiat on 2015-09-25
Its definitely a FlexRAID problem. I stopped the pool and went to the drive and it deleted successfully. No permissions needed to be changed though. Guess I need to track down this FlexRAID problem then.

---

### Post by rslater on 2015-09-25
> **frbastiat said:**
> Its definitely a FlexRAID problem. I stopped the pool and went to the drive and it deleted successfully. No permissions needed to be changed though. Guess I need to track down this FlexRAID problem then.

Maybe some file management task being carried out by the OS, that locks the files?  Good luck and glad you identified the problem.

---

### Post by frbastiat on 2015-09-25
Thank you for your help!

---

