---
title: "Unrar Password protected .rar files"
date: 2006-09-03
forum: General Help
---

### Post by iceman504 on 2006-09-03
hey i am using the newest ubuntu and i installed unrar (nonfree) and rar and i got 2 files thst require passwords but i cant get a place to enter the password in. any ideas?

---

### Post by cilynx on 2006-09-03
from the man page:

unrar -p<password>

---

### Post by pt123 on 2006-09-03
Why can't the Archive Manager - File Roller handle password RAR files. Its ridiculous.

---

### Post by iceman504 on 2006-09-03
ok thanks i figured it out but i ran into a new problem what about files that end with .z01 that are multipart files. In windows you could add .rar to the files(after .z01) and everything would extract with no problems but in ubuntu i only come up with errors or wont extract at all. any ideas on extracting these files?

---

### Post by starscalling on 2006-11-16
bump
i need this info too

---

### Post by matthew on 2006-11-16
I didn't see this thread the first time around...sorry.

There are several ways to accomplish what you want to do. For me the command line is the fastest and easiest and it is certainly the easiest way to tell you how to do it in a post like this.

First make sure the packages "rar" and "unrar" are installed. You can use the Synaptic Package Manager or open a terminal by going to Applications->Accessories->Terminal and typing```
sudo apt-get install rar unrar
```and entering your password when prompted.

To open password protected rar files from the command line first open a terminal and change to the directory the file is in.```
cd /directoryname
```then type```
unrar e filename.rar
```You will be prompted to enter the password.

Finally, for the multiple-file archives...hmm. I haven't dealt with those in a while so my memory is a bit fuzzy. Here are a couple of clues that will hopefully get you on the right track anyway. I believe that unrar should be able to handle the fact that there are multiple files and combine them for you. If there are several files, all with the same filename but differing extensions (filename.z01, filename.z02, etc) and one main filename.rar, then try ```
unrar e filename.rar
```If that doesn't do the trick you can try to join the separate files into one big file using cat```
cat filename.z* > groupedtogetherfilename.rar
```followed by```
unrar e groupedtogetherfilename.rar
```Anyway, hopefully that will help you with some ideas of where to look next if my ideas don't work for you right off the bat.

FINALLY: I'm moving this thread to General Help.

---

### Post by vliegje20 on 2007-01-19
I did what you said but at

unrar e filename.rar

it says:patrick@ubuntu:~/Desktop$ unrar e partykroegenhits.rar

UNRAR 3.51 freeware      Copyright (c) 1993-2005 Alexander Roshal

Cannot open partykroegenhits.rar
No files to extract
 im not asked for a password :(

---

### Post by Billquinn1 on 2007-01-19
Look for a program called HJsplit on the net. They have a linux version that will join them right up.

Bill

---

### Post by Billquinn1 on 2007-01-19
I just reread your post and I am wondering if you have installed the nonfree rar package. Look in synaptic and if you have not, then install it and try again.

Bill

---

### Post by Error1312 on 2007-01-19
There is also a commandline version of WinRar for linux which you can download here: [http://www.winrar.be/download.htm]("http://www.winrar.be/download.htm")

Simply extract it, and then use the following command:
rar e -p <filename of the first .rar archive>

It'll ask for a password and start extracting all the .rar archives.

---

