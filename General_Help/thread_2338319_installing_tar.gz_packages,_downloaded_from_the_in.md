---
title: "installing tar.gz packages, downloaded from the internet,  on ubuntu"
date: 2016-09-26
forum: General Help
---

### Post by Timothy_Cota on 2016-09-26
I have tried repeatedly to find instructions for installing a tar.gz file without success.  The problem is that linux geeks do not know how to talk down to newbies.  It is like trying to teach higher math to kindergarteners.   First you have to teach them to read and write.  You begin with two and three letter words.  You don't try to teach from the original King James Testament.
You start out with **** and Jane.  
The Instructions start  (paraphrasing)  After the package is extracted put it in the directory you want to use.  You have just jumped over the part that I can't figure out!  How to get the package from the download folder (or any other folder)  into a directory?!!  unktim

---

### Post by Bucky Ball on 2016-09-27
*Thread moved to **General Help**.*

Not to do with installing or upgrading Ubuntu.

It's in a directory already: /Downloads probably. Doesn't matter where it is. Create folder in /Downloads with the name of whatever it is you are downloading, download the .tar directly to there and extract the tar in there to keep it all in one place. 

Would help if you provided a link to what you are having trouble following and the exact bits you don't understand. You don't give much information and no information about what it is you are actually attempting to untar and where you are downloading that from.

---

### Post by howefield on 2016-09-27
> **Timothy_Cota said:**
> .....How to get the package from the download folder (or any other folder)  into a directory?!!  unktim

A .tar.gz is just a compressed bundle of files, similar to a .zip or .rar file in other operating systems.

Generally, double clicking on the .tar.gz file would bring up the Archive Manager and allow you to extract to your folder of choice, again similar to say, winzip or winrar in other operating systems.

---

### Post by Timothy_Cota on 2016-09-27
Thanks Bucky,  at first I thought it was a directory but then when I tried to install from there I got nothing but "directory does not exist.  I am beginning to think that that my 7 year old computer needs to be replaced.  I have a new computer on order so it will be interesting to see if that works any better.
 The first time I tried linux was when ubuntu 14:04 was released.  My wifes' HP had its' OS destroyed by a worm.  I had to wipe the hard drive clean and install a new OS so I thought It would be a perfect time to try linux.  I made a 14:04 boot disk and installed it.  It worked perfectly on her computer but when I installed it on my Toshiba I had quite a few problems.

---

### Post by Timothy_Cota on 2016-09-27
Hi Howerfield.  The archive manager does indeed extract tarballs well.  I just can never progress past that point.  I am starting to study "the linux command line" by Schott so maybe I will get better at using the terminal.    unktim

---

### Post by howefield on 2016-09-27
> **Timothy_Cota said:**
> Hi Howerfield.  The archive manager does indeed extract tarballs well.  I just can never progress past that point.  I am starting to study "the linux command line" by Schott so maybe I will get better at using the terminal.    unktim

If this thread is simply a general rant, then fine, but of you have a question then ask it :)

If you have an instruction that you don't understand then post it.

---

### Post by SeijiSensei on 2016-09-27
After you expand the archive, one of the items in it will be an executable file.  Run it with /path/to/the/file/filename.

I'd be very surprised if there isn't a version of the file already existing that you can install on Ubuntu either from the normal repositories or perhaps a PPA.  What program is it?

---

