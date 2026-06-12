---
title: "file permissions problem"
date: 2020-03-07
forum: General Help
---

### Post by duelistjp on 2020-03-07
i need new files in a directory to be created with permissions at least as free as 664.  my umask is currently 0003 and i have used setfacl in such a way that i thought it would be fine too but i keep getting new files with permissions of 744does anyone know what i am doing wrong or can suggest something I might have missed

---

### Post by TheFu on 2020-03-07
ACLs aren't inherited.

The umask should be 002 - this is the default.
It only works on Unix file systems, not NTFS, not exFAT or FAT32.

How are you creating new files?  Use the 'touch' program to see what Unix does.  Any other program can easily have different overrides.

Show the exact permissions, owner, groups you  have and what you want, please.
```
ls -al /path/to/directory
```
Use code-tags from the advanced editor here so the columns line up, otherwise it is too hard to read.

---

### Post by Morbius1 on 2020-03-07
I thought I'd post here just in case someone came up with a solution to this.

Haven't looked at this in a year or so but .......

The internal plumbing of Ubuntu does in fact set the default umask to 002. But if you open a terminal and run [highlight]umask[/highlight] that is not what you will see. You will see [highlight]022[/highlight]

Please note that I am talking specifically about Ubuntu. If you are running Ubuntu Server, Xubuntu, and as I recall Ubuntu MATE, and maybe KDE ( not sure about that one ) you will see the "correct" value of 002.

People have been reporting this bug all over the place - for many reasons. Here's one: [https://bugs.launchpad.net/ubuntu/+source/gnome-terminal/+bug/1685754](https://bugs.launchpad.net/ubuntu/+source/gnome-terminal/+bug/1685754)

Since I'm a Xubuntu user I don't much care since it works for me but I suspect most users run Gnome.

---

### Post by ajgreeny on 2020-03-07
I can confirm that ***touch newfile*** in Ubuntu will produce a file with -rw-rw-r--, ie, permissions of 664 as you want

Perhaps those permissions are different if the file is created in some other way, by another application.

---

### Post by Morbius1 on 2020-03-07
Nope.

Ubuntu Desktop:
> tester@vub1804:~$ umask
0022
tester@vub1804:~$ touch newfile
tester@vub1804:~$ ls -l newfile
-rw-r--r-- 1 tester tester 0 Mar  7 15:09 newfile

In my Xubuntu desktop:
> tester@vxub1804:~$ umask
0002
tester@vxub1804:~$ touch newfile
tester@vxub1804:~$ ls -l newfile
-rw-rw-r-- 1 tester tester 0 Mar  7 15:11 newfile

---

### Post by TheFu on 2020-03-07
Ubuntu-Mate
```
$ umask
0002
```

Same for Lubuntu and Server.  Don't know about the rest.
/etc/skel/.profile does have this line:
```
umask 022
```
but it is being overridden later.
That file points to libpam-umask and  /etc/profile.

OTOH, just change the default in ~/.profile (or whatever rc file your shell uses).

---

### Post by Morbius1 on 2020-03-07
That's why I said this:
>  Please note that I am talking specifically about Ubuntu. If you are  running Ubuntu Server, Xubuntu, and as I recall Ubuntu MATE, and maybe  KDE ( not sure about that one ) you will see the "correct" value of 002.
I will add Lubuntu to the list.

---

