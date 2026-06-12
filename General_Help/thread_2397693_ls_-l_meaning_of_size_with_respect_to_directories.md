---
title: "ls -l meaning of size with respect to directories"
date: 2018-08-02
forum: General Help
---

### Post by Alan5127 on 2018-08-02
Hi All,

This is just an 'out of interest' question.

If I do an ```
ls -l
``` command in a directory that contains sub-directories, I get an output like this:

drwxrwxrwx 1 root root      4096 Jan  6  2018 DirectoryA
drwxrwxrwx 1 root root          0  Aug  2 13:59 DirectoryB

As I have understood it up to now, the 'size' field (fifth field) is related to the number of files (and sub-directories recursively) inside that directory, but not to the size of the actual files.  It is, as far as I know, always a multiple of the drive block size, so usually a multiple of 1024 or 4096 or whatever.

So, in the above example, the 'size' of DirectoryA is 4096 and the 'size' of DirectoryB is 0.

However, DirectoryB is not empty - it contains a number of files, and in fact, it contains more files than DirectoryA which reports a larger size.

Based on my understanding, a directory with just one file in it would presumably have a 'size' of at least 1024 or 4096 (or whatever), but not zero.  Apparently my understanding is flawed.


I found these links which explain somewhat, but don't seem to address my actual question (unless I missed it or failed to understand which is quite possible!):

[URL="https://unix.stackexchange.com/questions/234065/why-size-reporting-for-directories-is-different-than-other-files/234293#234293"]https://unix.stackexchange.com/questions/55/what-does-size-of-a-directory-mean-in-output-of-ls-l-command

[/URL][https://unix.stackexchange.com/questions/234065/why-size-reporting-for-directories-is-different-than-other-files/234293#234293](https://unix.stackexchange.com/questions/234065/why-size-reporting-for-directories-is-different-than-other-files/234293#234293)


So what is going on?  How does it actually work?


Thanks,

Alan.

---

### Post by spjackson on 2018-08-02
> **Alan5127 said:**
> 
Based on my understanding, a directory with just one file in it would presumably have a 'size' of at least 1024 or 4096 (or whatever), but not zero.  Apparently my understanding is flawed.

A lot depends on the type of filesystem. If I create a new (and therefore empty) directory on an ext4 filesystem, its size shows as 4096. However, if I do exactly the same on NTFS, its size shows as 0. Which filesystem type are you asking about?

---

### Post by Alan5127 on 2018-08-02
Hi spjackson,

> **spjackson said:**
> A lot depends on the type of filesystem. If I create a new (and therefore empty) directory on an ext4 filesystem, its size shows as 4096. However, if I do exactly the same on NTFS, its size shows as 0. Which filesystem type are you asking about?


The one that is showing the results I posted above is NTFS.

Thanks,

Alan.

---

### Post by spjackson on 2018-08-02
I don't know a lot about the structure of NTFS. Maybe it's something to do with the [Master File Table]("https://en.wikipedia.org/wiki/NTFS#Master_File_Table")

It seems to me that on NTFS, if you create a new (and thus empty) folder, its size is reported as 0 bytes. If you create a file or folder within the new folder then empty it out again, the size remains non-zero but significantly less that 4096 - or maybe what happens here depends on which operating system writes to the NTFS filesystem.

Perhaps someone else knows more about the structure of NTFS and can explain fully the circumstance in which a directory's size is reported as 0 bytes.
[URL="https://en.wikipedia.org/wiki/NTFS#Master_File_Table"]
[/URL]

---

### Post by raleigh3 on 2018-08-02
> **spjackson said:**
> A lot depends on the type of filesystem. If I create a new (and therefore empty) directory on an ext4 filesystem, its size shows as 4096. However, if I do exactly the same on NTFS, its size shows as 0. Which filesystem type are you asking about?

Interesting. On my system an empty directory uses 0 bytes.

---

### Post by Alan5127 on 2018-08-02
Hi Raleigh3,

> **raleigh3 said:**
> Interesting. On my system an empty directory uses 0 bytes.


Do you see any directories that are not empty, but still showing zero file size from an ls -l ?

I have no issues with those directories - the files therein are fine, and can be accessed without any issues.

Thanks,

Alan.

---

### Post by QIII on 2018-08-03
Would you try to cd to the directory in question and run 

```
 ls -l
```

there?

You could also try

```
sudo du --max-depth=1 -hx /your/directory/here
```

If you want to drill down a bit more, increase the max-depth.  But that can end up giving you a lot more than you want.

---

### Post by Alan5127 on 2019-01-01
Just posting to say that I can no longer re-create this issue.

I am now running Ubuntu 18.04 LTS 64Bit, whereas before I was running Ubuntu 16.04 LTS 32Bit, so it seems likely that there is a difference between the two - not sure if it would be regarded as a bug in 16.04 or not - maybe just a different approach.

I am going to mark this as 'solved' on the above basis.

Thanks,

Alan.

---

