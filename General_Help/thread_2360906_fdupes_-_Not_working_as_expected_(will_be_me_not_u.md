---
title: "fdupes - Not working as expected (will be me not understanding)"
date: 2017-05-09
forum: General Help
---

### Post by Alan5127 on 2017-05-09
Hi All,

I am using the fdupes application to (try to) find duplicate files on a data drive.

Whilst I realise there are other options that I could install / use, I am really trying to improve my knowledge, and in particular, understanding why it is not working as I imagine it should, rather than just 'giving up and moving on'.

fdupes was not installed by default on my Ubuntu 16.04LTS - I installed it using apt.

I run the following command:

```
fdupes -r /pathto/folder100/
```

It finds (found) some duplicates, which I have resolved / deleted as appropriate, but I know for certain that there are others it is not finding such as:

/pathto/folder100/folder120/folder123/file1234.txt
/pathto/folder100/folder130/file1234.txt

The filenames are identical, which is what I want to identify (in some cases, the files might have the same name, but be different - I am always manually checking all the identified duplicates before resolving, which might include renaming a file).

Is there any way to get fdupes to identify file1234.txt is a dupicate (filename) across the folder100 hierarchy of folders and sub-folders?

Thanks in advance,

Alan.

---

### Post by TheFu on 2017-05-10
Are you sure they really are the same?  An extra byte matters.
Does 'diff' prove sameness?

---

### Post by Alan5127 on 2017-05-10
Hi TheFu,

No - they could be different files, but I am trying to identify duplicate filenames (even if the content differs).

Thanks,

Alan.

---

### Post by TheFu on 2017-05-10
I think that is a different problem.  Not hard to solve. Use **dirname** and **basename** to split the filenames up. Then just sort on the filename.

filename\tdirname

is how I'd do it. It would be a 1 line **find** cmd, methinks.  Might take more. Not something I've tried to solve, since there are thousands of same-named files on my systems.  The directory they are in IS the difference.

---

### Post by Alan5127 on 2017-05-10
Hi TheFu,

Sorry - I am not sure how to do that.

Could you give me an example such as (but obviously not):

fdupes -r /pathto/folder100/

Thanks,

Alan.

---

### Post by TheFu on 2017-05-10
Sorry, I don't understand your question.
Use a **find** command. There are thousands of examples online.
That will fill in a {} variable which can be used in **dirname** and **basename** tools. Use both of those to get the directory and filename.  Print those out as 
```
filename {tab} directory
``` which can be redirected into a working file (any name you want, /tmp/ is a good place for it.  Sort that file - bam, you have all the same named files, together.

O'Reilly has a *Unix Power Tools* book which explains this sort of scripting pattern. It has been around for 20+ yrs. That's how I learned this stuff.  All those concepts still work on Linux. I'd be surprised if a library didn't have it. The version from 1990 would be just as good as a version from 2016.
Many businesses have logins for their IT people which provide access to online books. Might check there too. Chpt 45 has dirname/basename.

---

### Post by Alan5127 on 2017-05-10
Hi TheFu,

As I mentioned in my original post, there are probably lots of ways to do this, but I am specifically wanting to understand fdupes better.

Are you saying that fdupes cannot achieve the outcome I am looking for, and I must go with another option (such as 'find')?

Thanks again,

Alan.

---

### Post by TheFu on 2017-05-10
No. I'm not saying that.  The nature of that program is to find identical, duplicate, files. 

[https://linux.die.net/man/1/fdupes](https://linux.die.net/man/1/fdupes) 
```
Description
Searches the given path for duplicate files. Such files are found by comparing 
file sizes and MD5 signatures, followed by a byte-by-byte comparison.
```
doesn't show any options to do what you want that I see.  The description is pretty clear.  File size and MD5 signatures are what they use.

---

### Post by Alan5127 on 2017-05-10
Hi TheFu,

I hadn't spotted that.  As you say, it looks like fdupes is not designed to achieve what I am wanting to do.

Thanks for your assistance,

Alan.

---

### Post by dragonfly41 on 2017-05-11
fslint might help you ..

[http://sourcedigit.com/17855-how-to-find-remove-duplicate-files-in-linux-ubuntu-systems/](http://sourcedigit.com/17855-how-to-find-remove-duplicate-files-in-linux-ubuntu-systems/)

although be advised that I have not been able to install fslint on Ubuntu 16.04 due to some dependency (I suspect because I have python 3.6 version as default)

```
fslint-gui  File "/usr/bin/fslint-gui", line 182
    except getopt.error, msg:
                       ^
SyntaxError: invalid syntax

```

[Edit]
Found the reason for the error ... [https://bugzilla.redhat.com/show_bug.cgi?id=1078663](https://bugzilla.redhat.com/show_bug.cgi?id=1078663)

fslint requires python 2.7.

As a quick fix to force usage of python 2.7 instead of python 3  I edited namespace in /usr/bin/fslint-gui.py to be
#!/usr/bin/env python[COLOR=#ff0000]**2.7**[/COLOR]

and in a couple of fslint scripts found in  /usr/share/fslint/fslint/fslint

Then I could launch fslint-gui from command line.

---

