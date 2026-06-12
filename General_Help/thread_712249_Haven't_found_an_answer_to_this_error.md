---
title: "Haven't found an answer to this error"
date: 2008-03-01
forum: General Help
---

### Post by shahgols on 2008-03-01
Hi all,

Been searching and searching google and all sorts of forums for this problem that I'm having without luck.  I'm trying to run an application and get the following error:

[root@localhost bin]# ./Toke*
./TokenManager: error while loading shared libraries: ../../../../j2sdk/jre/lib/i386/libjsig.so: cannot open shared object file: No such file or directory

I'm running Linux Mint 4.0 (I know, it's not exactly Ubuntu, but there are a ton more people here).  Any help would be HIGHLY appreciated.  Thanks.

---

### Post by Whiffle on 2008-03-01
Hmmm.  Assuming you've got libjsig.so on your computer

check that with:

locate -u

locate libjsig.so

If its there, then its not finding it.  What gets me is this
../../../../
on that line you posted.  It looks like its trying to go 4ish directories up the tree, then looking for /j2sdk/jre/lib/... ,hmm.

---

### Post by shahgols on 2008-03-01
Hi Whifle, 

I have the libjsig.so on the computer in 3 different directories.  I have added those directories to the PATH but I guess that the application that I am trying to run is looking for a specific one.  

Also, I can't find any directory or file on my computer that has j2sdk in it.

---

### Post by shahgols on 2008-03-01
Just downloaded and installed the Java sdk.  Now I have a /usr/lib/jvm/j2sdk directory.  Actually, the file libjsig.so exists at /usr/lib/jvm/j2sdk/jre/lib/i386/libjsig.so.  When I open the file that I am trying to run in vi, I see a whole lot of weird characters.  I searched for "j2sdk" and I found it within the file.  It's hard coded as ../../../../j2sdk/jre/lib/i386/libjsig.so.  Can I change that to /usr/lib/jvm/j2sdk/jre/lib/i386/libjsig.so in vi or will that break the file?

---

### Post by Whiffle on 2008-03-02
Usually when I want to try something I'm not sure about, i'll comment it out and replace it.  That way if the new one doesn't work, its easy to fix again.  Go ahead and make the change, I bet it'll work.  Sounds like some crappy programming on their part though.

---

