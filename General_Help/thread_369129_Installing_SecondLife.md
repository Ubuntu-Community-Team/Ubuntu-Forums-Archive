---
title: "Installing SecondLife"
date: 2007-02-24
forum: General Help
---

### Post by OsakaWilson on 2007-02-24
Anyone know how to install SecondLife? I got the file from the SecondLife page and tried to install it based on directions from the forum, but they didn't work. 

**Directions that didn't work #1:**
In the terminal, go to the directory where you downloaded the file (.tar.bz2) and:
tar jxvf SecondLife(etc).tar.bz2
cd SecondLife(etc)
./configure
make
sudo make install
(enter your user password here)

**Directions that didn't work #2:**
1. unpack
tar -xjf /SecondLife.filename
2. cd <tab> SecondLife
3. ./secondlife
4. Wait for error messages, scratch head
5. Hit the SL Linux forums
6. I had to edit xorg.conf a bit; but your results and mileage may vary

**My error message:**
??????@???????-desktop:~$ tar -xjf /SecondLife_i686_1_13_3_2.tar.bz2
tar: /SecondLife_i686_1_13_3_2.tar.bz2: Cannot open: No such file or directory
tar: Error is not recoverable: exiting now
tar: Child returned status 2
tar: Error exit delayed from previous errors

Installing packages never works for me if it is not a deb file. Help?

---

### Post by Maestro23 on 2007-02-24
.

---

### Post by energiya on 2007-02-24
> **OsakaWilson said:**
> 
**My error message:**
??????@???????-desktop:~$ tar -xjf /SecondLife_i686_1_13_3_2.tar.bz2
tar: /SecondLife_i686_1_13_3_2.tar.bz2: Cannot open: No such file or directory
tar: Error is not recoverable: exiting now
tar: Child returned status 2
tar: Error exit delayed from previous errors

It should be  
```

tar -xjf SecondLife_i686_1_13_3_2.tar.bz2

```
without the "/", if the file is in the folder you are. And do this in a folder you have permissions, and also check the permisions of the file.

Why didn't the first method work?

---

### Post by HereInOz on 2007-02-24
I know nothing about SecondLife or the process of its installation, but have you checked the permissions on the tar file.  It could be that you do not have permission to open the tar file.

Also, is that error happening when you unpack, or when you try to install after unpacking?  It looks like it is after you have unpacked.  If that is the case, then I wonder why the process returning the error is looking at the tar file, when my feeling is that it should be looking at the unpacked files from the tar, wherever they have been put.

Wish I knew the application and its install process, and could help more.

---

### Post by OsakaWilson on 2007-02-24
**Energiya,**
I tried removing the slash and got this:

??????@??????-desktop:~$ tar -xjf SecondLife_i686_1_13_3_2.tar.bz2
tar: SecondLife_i686_1_13_3_2.tar.bz2: Cannot open: No such file or directory
tar: Error is not recoverable: exiting now
tar: Child returned status 2
tar: Error exit delayed from previous errors

The file is definitely on my desktop.


**HereInOZ,**
I don't know what unpacking means. The file was as it appeared on my desktop after downloading it. I double-clicked it to see what happened and then extracted it to the desktop. Now I have a folder and the original red box thing that I had before. 

I don't know how to get permission for something or how to tell if I have it or not.

---

### Post by Maestro23 on 2007-02-24
EDIT: Cappy gave by-the-numbers help.

---

### Post by Cappy on 2007-02-24
I'll assume you start at HOME (~)
The problem is you are not changing to your Desktop directory.
The file may also be named differently from what it is in the tutorial.
Let's go step by step.
cappy@cappychan:~$ cd Desktop/Second (Hit Tab) (Then Press Enter)
you should now see this prompt similar to this:
cappy@cappychan:~/Desktop/SecondLife_i686_1_13_3_2$
If you don't see something like that you're in the wrong folder! use "ls -l" to see a directories files and folders and "cd Desktop" for instance to change to a directory.
Also, know that folders and files are case-sensitive. If you tried to do a "cd desktop" it would be wrong because "Desktop" is capitalized.

Now all you should need to do is this:
./secondlife

All you're doing is switching to SecondLife's directory and running the file.
By opening the folder on your desktop and just double clicking "secondlife" it will probably run also.
Good luck =)

---

### Post by g8m on 2007-02-24
Doesn't Nautilus or mc open gzipped files. When I doubleclick under kde on such a file, ark opens it and i can unpack it.

I used it once, and if I recall you just have to unpack it and run it from the unpacked directory.

---

