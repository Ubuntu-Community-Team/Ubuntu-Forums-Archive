---
title: "TrueCrypt?"
date: 2012-12-23
forum: General Help
---

### Post by d4m1r on 2012-12-23
Hey guys, I am looking to password protect an external NTFS formatted USB harddrive and I've read TrueCrypt is a popular solution to do so....I have installed the linux version of the client and will be reformating the drive with password protection enabled but my question is, do I need to have the client installed to access the drive?

For instance, I also have a Windows and OS X machine so will I have to install the TrueCrypt client on those OS's as well, or when I connect the drive, will it just ask me for a password? :confused:

---

### Post by ranger1021994 on 2012-12-23
Yes you need to have truecrypt client installed

---

### Post by haqking on 2012-12-23
> **d4m1r said:**
> Hey guys, I am looking to password protect an external NTFS formatted USB harddrive and I've read TrueCrypt is a popular solution to do so....I have installed the linux version of the client and will be reformating the drive with password protection enabled but my question is, do I need to have the client installed to access the drive?

For instance, I also have a Windows and OS X machine so will I have to install the TrueCrypt client on those OS's as well, or when I connect the drive, will it just ask me for a password? :confused:

> **ranger1021994 said:**
> Yes you need to have truecrypt client installed

no you dont, you can run it in portable mode.

[http://www.truecrypt.org/docs/truecrypt-portable](http://www.truecrypt.org/docs/truecrypt-portable)

---

### Post by d4m1r on 2012-12-26
Thanks for the replies guys, I now have been able to setup TrueCrypt across linux, windows, and os x...

The problem I am now having is linux keeps corrupting my encrypted partition that I use for backups....I can copy files under Windows and OS X fine, but the partition almost always corrupts itself after I mount it under Ubuntu 12.04....I get no errors when mounting it and it can read/write to it fine. Just when I go to mount it on Windows or OS X after it was mounted on linux, it is almost always corrupted....Anyone else had this problem?

I think it may be related to de-mounting it....I demount it via TrueCrypt and then use pull the USB HDD out as it is no longer visible in nautilus...Is this wrong? :confused:

---

