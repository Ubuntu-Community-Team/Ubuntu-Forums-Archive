---
title: "Security ? - confused"
date: 2006-10-18
forum: General Help
---

### Post by wilko10 on 2006-10-18
I'm confused about linux security. I kept a spare partition for edgy and installed it at the weekend so I can dual boot with dapper.
Installed as new user and its fine.
/home is a seperate partition so has a sepeate directory for each user a dapper one and an edgy one.
However I was able to cut/paste from the dapper user to the edgy user, my MP3's and various documents etc.
So does this mean anyone could 'steal' a server they dont know how to log-on to, shrink a partition with gparted live disk say, install a version of linux in the space freed up, boot into it and steal all the data?
It seems wrong or i've missed something.
anyone?
J

---

### Post by mcduck on 2006-10-18
> **wilko10 said:**
> I'm confused about linux security. I kept a spare partition for edgy and installed it at the weekend so I can dual boot with dapper.
Installed as new user and its fine.
/home is a seperate partition so has a sepeate directory for each user a dapper one and an edgy one.
However I was able to cut/paste from the dapper user to the edgy user, my MP3's and various documents etc.
So does this mean anyone could 'steal' a server they dont know how to log-on to, shrink a partition with gparted live disk say, install a version of linux in the space freed up, boot into it and steal all the data?
It seems wrong or i've missed something.
anyone?
J

As long as somebody can get a physical access to your computer your data is never safe, no matter what OS you are running or how you set permissions for files. Most of the time just booting a linux live-cd will give access to all data on a computer. And even if booting from CD is not possible, somebody could just remove the drive from your machine, put it into another one and open the content that way. And even crypted content is not impossible to open. 

So only way to keep your data _really_ safe is to make sure nobody has physical access to your machine :)

---

### Post by po0f on 2006-10-18
wilko10,

```
$ chmod 700 ~
```
will make your home folder only viewable by you.  Unless your Dapper and Edgy users share the same UID, this should not allow you to copy/paste stuff between the home folders.

---

### Post by Jussi Kukkonen on 2006-10-18
Two issues here:
1. default file creation attributes give "others" read access to new files, so any other user can read your documents. This an be changed.
2. The physical access issue mcduck refers to is practically impossible to overcome -- with default settings just booting a ubuntu machine into single user mode gives anyone root access... 

Even if that wasn't the case the attacker could make USB or CD bootable in BIOS (almost nobody protects their BIOS with a password), and boot into another OS and mount the disks. Even if BIOS is locked the attacker can open the case, plug the disk into another computer and read the files...

---

### Post by mcduck on 2006-10-18
> **Jussi Kukkonen said:**
> 
Even if that wasn't the case the attacker could make USB or CD bootable in BIOS (almost nobody protects their BIOS with a password), and boot into another OS and mount the disks. Even if BIOS is locked the attacker can open the case, plug the disk into another computer and read the files...

..not to mention that BIOS password can most of the times be cleared simply with 'clear CMOS' jumper on the motherboard, or by removing CMOS battery for a while..

---

### Post by anthro398 on 2006-10-18
> **po0f said:**
> wilko10,

```
$ chmod 700 ~
```
will make your home folder only viewable by you.  Unless your Dapper and Edgy users share the same UID, this should not allow you to copy/paste stuff between the home folders.


This is not correct.  Booting from a livecd, sudo su, and all your file are belong to me.  The real answer, outside of securing physical access, is encryption.

---

### Post by po0f on 2006-10-18
anthro398,

And here I thought it was implied that a root user has access to the whole filesystem...  Just to reiterate:

**WARNING** The root user has access to the *whole* filesystem. **/WARNING**

---

### Post by anthro398 on 2006-11-08
> **po0f said:**
> anthro398,

And here I thought it was implied that a root user has access to the whole filesystem...  Just to reiterate:

**WARNING** The root user has access to the *whole* filesystem. **/WARNING**


See, the thing is that even your quote above doesn't go far enough.  I mean, I can lock down the root account on my system until the cows come home.  Someone does not have to gain access to **my ** root account.  Someone can instead boot from a CD and use the root account from that OS.  So the fact is that anyone with physical access to your machine can gain full access unless you've encrypted your data.  BIOS passwords, boot passwords, permissions, firewalls, etc, are all just minor stumbling blocks.  All of these are easily defeated even by beginners who know how to search the internet and have physical access.

---

### Post by bsussman on 2006-11-08
> **wilko10 said:**
> However I was able to cut/paste from the dapper user to the edgy user, my MP3's and various documents etc.


The comments re physical security are correct:  pyysical access = I can access anything that is not encrypted.

But there is another point that has not been raised.

I am assuming you are talking about cut/paste from your first (only?) user in 6.06 t/f your first (only?) user in 6.10.

If so, no matter what the 'name' of the user is, the userid is going to default to 1000 and this is what the security system uses (not the name) to authorize access.  Unless you changed it, uid xxxx  owns all your two user's files.  For example, on our 3 home machines, my wife is uid 1001 and I am # 1000 on all of them.

try 'ls -n' in various directories and compare to the contents of /etc/passwd for verification.

Generally this is a good thing - I really do not want to have to use root to coordinate arount many machines when it is my own user stuff that I am maintaining.  Many organizations use something like an employee# as userid for this reason.

---

