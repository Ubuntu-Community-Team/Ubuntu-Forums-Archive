---
title: "Need help installing Veritas NetBackup"
date: 2007-05-07
forum: General Help
---

### Post by jester805 on 2007-05-07
I just installed Feisty Fawn on my Dell Laptop.  We use Veritas NetBackup Enterprise at work.  I have a Linux installation CD, but I cannot seem to get it installed.

First off, it doesn't like installing from the CD.  I have to copy the contents of the CD to my hard drive.  So I make a new directory in my home directory and do this from within the CD-ROM's directory:

```
 sudo cp -Rp * ~/nb
```

After the copy is complete, I change to the ~/nb directory and do:  sudo ./install
That brings up Installation Options.  I want to install the NetBackup Client Java Software, but I have to install the NetBackup Client first.  That install seems to finish successfully.  It's when I try to run the Java Client install that I get problems.  Here is what I get:

> VERITAS Installation Script
Copyright 1993 - 2003 VERITAS Software Corporation, All Rights Reserved.

        Installation Options

        1 NetBackup
        2 NetBackup Client Software
        3 NetBackup Client Java Software

        q To quit from this script
Choose an option [default: q]: 3

cp NB-Java.tar.Z /usr/openv/NB-Java.tar.Z
cp Linux_JRE.tar.Z /usr/openv/java/Linux_JRE.tar.Z
cp libSigScheduleJNI.so /usr/openv/lib/server/linux/libSigScheduleJNI.so
Installing NB-Java.
zcat: /usr/openv/java/Linux_JRE.tar.Z: No such file or directory
zcat: NB-Java.tar.Z: No such file or directory



Any help would be great!!
Thanks!

---

### Post by jester805 on 2007-05-08
bump

---

### Post by jholzman on 2007-07-06
I got help here in the forum for Netbackup client on 6.10.  It works for 6.10, but not for 7.04.  I need help to get 7.04 working.  

To get it installed.
cd Linux/RedHat2.4 directory, then vi cp_to_client
remove the rc.d part and save.  It will install now.

Your going to need the Netbackup patch MP3.

and

xinetd with dependences
libc6-i386 with dependences.  I use libc6-i686 with my 7.04.
libstdc++2.10 with dependences.

It still blows up and refuses connection bpbrm.  I have not figured out why yet.

---

### Post by ksudbury on 2007-11-12
Hi did you get this working with dapper in the end? I am looking to roll out a remote client to a dapper box... 


Cheers

---

