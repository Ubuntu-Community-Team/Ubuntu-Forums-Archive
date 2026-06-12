---
title: "find command with -cnewer test doesn't behave as expected"
date: 2017-08-07
forum: General Help
---

### Post by John_Patrick_Mason on 2017-08-07
According to the Linux command line book I'm reading now, -cnewer *file *with the find command is supposed to match files or directories whose contents or attributes were last modified more recently than those of *file*. However, if I have a directory named Pictures with the following contents:

```

cd Pictures
ls -lht
total 6.5M
drwxrwxr-x 2 mason mason 4.0K Mar 18 16:55 Wallpapers
-rw-r--r-- 1 mason mason 210K Nov 27  2016 file1.jpg
-rw-r--r-- 1 mason mason 245K Nov 27  2016 file2.jpg
-rw-r--r-- 1 mason mason 805K Feb 27  2015 file3.jpg
-rw-r--r-- 1 mason mason 145K Jan 15  2015 file4.jpg
-rw-r--r-- 1 mason mason 1.9M Jun 14  2014 file5.jpg
-rw-r--r-- 1 mason mason 675K Jun 14  2014 file6.jpg
-rw-r--r-- 1 mason mason 404K Jun 14  2014 file7.jpg
-rw-r--r-- 1 mason mason 1.5M Sep 20  2013 file8.jpg
-rw-r--r-- 1 mason mason 348K May 27  2013 file9.jpg
-rw-r--r-- 1 mason mason  26K May 27  2013 file10.jpg
-rw-r--r-- 1 mason mason 8.6K May 26  2013 file11.jpg
-rw-r--r-- 1 mason mason 155K Apr  2  2013 file12.jpg
-rw-r--r-- 1 mason mason 6.7K Apr  2  2013 file13.jpg
-rw-r--r-- 1 mason mason  20K Mar  9  2013 file14.jpg

```

and then type:

```

find . -type f -cnewer file4.jpg

```

it shows me every single file, instead of the newer files (files 1,2, and 3).

Could anybody explain?

---

### Post by spjackson on 2017-08-09
As I understand it, you are referencing two different timestamps of the files. Your ls command shows the timestamp of the last modification to the file **content** whereas -cnewer references the last modification time of the **inode** (e.g. via chmod). To compare like with like use
```

ls -lht[B]c
[/B]
```
or if you want to stick with ls -lht (using the modification time of the file **content**) then use
```

find . -type f **-newer **file4.jpg

```

---

### Post by John_Patrick_Mason on 2017-08-09
Just to be clear on the terminology, when you say "the last modification time of the inode," you mean the timestamp of the metadata associated with the inode, am I right?

---

### Post by spjackson on 2017-08-10
Probably. I mean this:
```

$ man ls
...
       -c     with  -lt:  sort by, and show, ctime (time of last modification of
              file status information); with -l: show ctime and  sort  by  name;
              otherwise: sort by ctime, newest first

```
or this...
```

$ man find
...
       -cnewer file
              File's status was last changed more recently than file  was  modi&#8208;
              fied.   If  file  is  a  symbolic link and the -H option or the -L
              option is in effect, the status-change time of the file it  points
              to is always used.

```
or this
```

user@bbox:~$ stat a_file
  File: ‘a_file’
  Size: 133           Blocks: 8          IO Block: 4096   regular file
Device: 805h/2053d    Inode: 24510625    Links: 1
Access: (0777/-rwxrwxrwx)  Uid: ( 1000/    user)   Gid: ( 1000/    user)
Access: 2017-08-04 09:25:10.270663745 +0100
Modify: 2010-02-22 18:25:56.000000000 +0000
**Change: 2011-11-06 19:36:35.679914992 +0000**
 Birth: -
user@box:~$ ls -l a_file
-rwxrwxrwx 1 user user 133 Feb 22  2010 a_file

```

---

### Post by John_Patrick_Mason on 2017-08-11
OK, so I did some limited testing using the -cnewer test.

This is what I did. I typed:

```

cd ~/Documents
touch file1.txt

```

then waited a few minutes, and then did:
```

touch file2.txt

```

and then compared the content and metadata timestamps to each other by doing:

```

ls -lht
-rw-rw-r-- 1 mason mason    0 Aug 11 01:19 file2.txt
-rw-rw-r-- 1 mason mason    0 Aug 11 01:17 file1.txt

ls -lhtc
-rw-rw-r-- 1 mason mason    0 Aug 11 01:19 file2.txt
-rw-rw-r-- 1 mason mason    0 Aug 11 01:17 file1.txt

```

so far no surprises. But what if I type:

```

chmod 664 file1.txt

```

to change the metadata timestamp, and then look at the output again:

```

ls -lhtc
-rw-rw-r-- 1 mason mason    0 Aug 11 01:23 file1.txt
-rw-rw-r-- 1 mason mason    0 Aug 11 01:19 file2.txt

```

file1.txt  appears in first position in the "ls -lhtc" output, but still in second  position in the "ls -lht" output, also as expected.
What I basically  did by typing "chmod 664 file1.txt" was to change the metadata  timestamp without touching the content timestamp.
Now, if I decide to type:

```

cd ~/Documents
find . -cnewer file1.txt

```

I get:

```

.
./file2.txt
./file1.txt

```

Since file1.txt is the most recent file in the metadata timestamp output after applying chmod on it, file1.txt shouldn't end up in the output when using the find command *solely* because of its position in the metadata timestamp output, since there is no more recent file. And since -cnewer also searches for files with a more recent *content* timestamp than file1.txt, file2.txt ends up in the output. The question I have is, how come file1.txt also ends up in the output when using the find command with the -cnewer test? Does the find command print the argument (file1.txt) used with the -cnewer test by default?

---

