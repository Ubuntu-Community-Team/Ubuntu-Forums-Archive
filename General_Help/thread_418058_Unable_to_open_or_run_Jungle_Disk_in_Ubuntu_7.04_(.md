---
title: "Unable to open or run Jungle Disk in Ubuntu 7.04 :( (new)"
date: 2007-04-22
forum: General Help
---

### Post by enthusaroo on 2007-04-22
I was an avid Windows user all of my life until I decided to switch to Linux a few days ago. I installed Ubuntu 7.04 "Feisty Fawn" when it was released on the 19th.

I used Jungle Disk everyday on Windows for more than a year. I can honestly say it's one of my "can't live without" programs. If I am going to continue using Ubuntu, I need to be able to get Jungle Disk working.

Jungle Disk is a GUI program that makes it easy to backup files to Amazon's S3 online storage service.
[http://www.jungledisk.com](http://www.jungledisk.com) 
I posted this question over at the jungledisk.com forums too, but I figured I'd cross-post here just to see if anyone in this community has any experience with this application.

It may be because I'm new to Linux / Ubuntu and therefore maybe I don't know what I'm doing or perhaps I'm just doing something the wrong way. Basically, I download the latest Jungle Disk for Linux, then I extract it, and next I try just double-clicking on the "jungledisk" program - nothing happens. After that I reread the instructions again. I verify that I have openSSL installed on Ubuntu. Yup, it's there.

I run the following commands:
ln -s /lib/libcrypto.so.0.9.8a /lib/libcrypto.so.0.9.7
ln -s /lib/libssl.so.0.9.8a /lib/libssl.so.0.9.7

Still it doesn't work. I try running Jungle Disk in the Terminal program:
shaun@Shaun-Linux:~/jungledisk$ sudo sh jungledisk
jungledisk: 1: Syntax error: "&" unexpected (expecting ")")

What am I doing wrong? Why can't I get Jungle Disk to open or run? I really need this program to work on Ubuntu. This is the program that will either "make it or break it" for me with deciding to use Linux.

Any idea how to make Jungle Disk work? What am I doing wrong?

---

### Post by tictacman on 2007-04-22
I had a quick look for you. The file that gets downloaded is a compressed file, a bit like zip.  You need to uncompress it first either by right clicking and selecting a program such as xarchiver or opening up a shell window and in folder in which it is located (I downloaded to my home folder so I didn't need to hunt for it) uncompress it with a command:

tar -zxvf junglediskbeta.tar.gz

you end up with a folder in which you can find an INSTALL document and a script called junglescript.  You can run the script in the shell window by typing ./junglescript.

BE AWARE: You might get errors if you haven't got the necessary packages. As it says on the jungledisk webpage you need:

Requires Linux x86 with KDE or GNOME desktop (GTK2 libraries)

---

### Post by tictacman on 2007-04-22
Hmm.  I see what you mean. Doesn't work for me either.  Are you running a 64bit machine.  A quick google tells me 64 bit users have experienced similar errors.

Have you read this thread on the jungledisk forum yet:

[http://forum.jungledisk.com/viewtopic.php?t=3490](http://forum.jungledisk.com/viewtopic.php?t=3490)

---

### Post by ashz on 2007-04-22
Alternatives...

[http://jeremy.zawodny.com/blog/archives/007641.html](http://jeremy.zawodny.com/blog/archives/007641.html)

cheers
ash

---

