---
title: "command not found - feisty"
date: 2007-08-26
forum: General Help
---

### Post by zugg on 2007-08-26
I've installed two apps in Feisty and am getting a "command not found" response when I try to run them.

the files are there and the permissions are correct ( [d]rwxr-xr-x on the entire structure and all the files, owned by root)  I've tried sudo ./rush and get the same thing.... I'm not having perm errors, just "command not found".

I am able to ls the file using tab completion both from within the directory and from elsewhere, ie

ls /usr/local/rush/bin/r  [tab] will comlete to /usr/local/rush/bin/rush

or from within /usr/local/rush/bin  if i type  ./r [tab] it will complete to ./rush

yet, each time it will yield "command not found"

i've tried installing to a different directory (outside of /usr, etc) and have chmod -R 777 /usr/local/rush  just in case.  No dice.  I'm having this problem with another app as well.  

the *crazy* thing is both of these apps installed under Dapper Drake, FC6, Debian 4, CentOS 4.5 and CentOS 5 had no issues at all

I've seen other forum posts with similar issues but none had a resolution.  I wanna use Feisty for many reasons but must use CentOS 5 as I can't get any work done.

I'm using 7.04 desktop edition for x86_64 (and I installed these same apps under the 64 bit versions of the distros listed above).  i've tried csh and tcsh as well.

---

### Post by jamvegan on 2007-08-27
I was trying to figure out what the program rush was, since I'd never heard of it.  What I found by Googling ([here]("http://seriss.com/rush.102.14/rushd-unix-install.html"), for instance) appears to be a daemon, which has to be started with an init script.  Is your rush a different program?

---

### Post by zugg on 2007-08-27
yup, it's a program for queueing/rendering frames on a render farm.  I've requested help from the creator from whom I purchased the software, however, it's not only happening with this program but another program as well (made by a different company) and as they both run fine in every other distro I've tried (including another version of Ubuntu) it leads me to believe it has to do with Feisty, not the programs themselves.

---

### Post by kellemes on 2007-08-27
Did you try with sudo?

---

### Post by zugg on 2007-08-27
yeah, i've tried sudo and had no luck.  :(

from line two of my original post...

>> the files are there and the permissions are correct ( [d]rwxr-xr-x on the entire structure and all the files, owned by root) I've tried sudo ./rush and get the same thing.... I'm not having perm errors, just "command not found".

---

### Post by kellemes on 2007-08-27
> **zugg said:**
> yeah, i've tried sudo and had no luck.  :(

from line two of my original post...

>> the files are there and the permissions are correct ( [d]rwxr-xr-x on the entire structure and all the files, owned by root) I've tried sudo ./rush and get the same thing.... I'm not having perm errors, just "command not found".

Guess I was blind for a minute.

---

### Post by zugg on 2007-08-28
SOLUTION!

I had two very seasoned sys admins looking into this.  the result was both apps i was trying to run were 32bit, in 64bit feisty.  apparently unlike ubuntu 6.06 LTS the proper 32bit libraries are not installed by default.  running the following seems to have fixed everything.


apt-get install ia32-libs ia32-libs-gtk ia32-libs-kde


what's whack is that there were no "lib" errors, just "command not found"

---

