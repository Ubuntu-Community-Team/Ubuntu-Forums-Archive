---
title: "command line is NOT case sensitive"
date: 2007-03-27
forum: General Help
---

### Post by umonkey on 2007-03-27
The command line in Ubuntu appears to *not* be case sensitive. 

For example typing "touch HELLO" creates a file named "hello" instead of "HELLO". Also, typing "rm hello" will delete a file named hello regardless of case.  (i.e. HELLO, Hello, HeLLo, would all be deleted). 

I've never noticed this before. But yesterday I was trying to create a directory in ALL CAPS, and the &@%!# thing wouldn't let me! I can't tell you how #!@%$ annoying this is. This is Linux, not MS DOS. What genius decided it was necessary to emulate that obsolete piece of cr@p? :evil: 

More importantly, how can I turn off this behavior and make the command line case sensitive again?

---

### Post by fanatik on 2007-03-27
which filesystem are you running this command on?

type:
pwd
mount

and paste the output

James.

---

### Post by umonkey on 2007-03-27
/dev/sda5 on /media/share type vfat (rw,utf8,umask=007,gid=46)

It is a VFAT file system that I share between OS when dual-booting. Does using VFAT force this behavior?

---

### Post by oracle5 on 2007-03-27
I have the same problem with fat drives. Its still case sensitive for linux filesystems.

---

### Post by devils_casper on 2007-03-27
> Does using VFAT force this behavior?
yes, try touch command in Linux native filesytem. it wont behave that way.

---

### Post by taurus on 2007-03-27
```
cd ~
touch HELLO
ls -la HELLO
```

---

### Post by Ramses de Norre on 2007-03-27
FAT is case insensitive, so it isn't your shell but your file system which is responsible.

---

### Post by umonkey on 2007-03-27
Bummer.  :( 

FAT can store both upper case and lower case in file names.  So I don't understand why the driver wasn't coded so that bash can behave like a Unix shell as much as possible when working with a FAT file system. 

Anyway, thanks for clearing that up.

---

### Post by dcstar on 2007-03-27
> **umonkey said:**
> 
FAT can store both upper case and lower case in file names.  So I don't understand why the driver wasn't coded so that bash can behave like a Unix shell as much as possible when working with a FAT file system..

Because it **wouldn't** be a FAT filesystem if it was case sensitive.

If you want to complain to someone about how FAT filesystems work, his name is B.Gates and he made it this way in the original PC-DOS filesystem (which FAT is backward compatible with).

---

### Post by ®om on 2007-03-29
I have the same problem:

I would like to share my files between windows et linux, I use a FAT32 partition.

But, under kubuntu, I have a problem: case sensitiviy is ok except if it is ALL CAPS.

For example:
```
rom1v@rom1v-desktop:/media/d/test$ ls
rom1v@rom1v-desktop:/media/d/test$ mkdir SalutToi
rom1v@rom1v-desktop:/media/d/test$ ls
SalutToi
rom1v@rom1v-desktop:/media/d/test$ mkdir SALUT
rom1v@rom1v-desktop:/media/d/test$ ls
salut  SalutToi
rom1v@rom1v-desktop:/media/d/test$
```
It is a **[SIZE="6"]huge[/SIZE]** problem for me because for my shared java project by CVS, CVS data MUST BE in a "CVS" subdirectory, but not a "cvs" one (eclipse don't find them in that case).

Here is the line of my hdd in /etc/fstab:
```
/dev/sda5       /media/d        vfat    rw,user,auto,exec,gid=100,uid=1000,umask
=002,utf8,codepage=850  0
```
I tried also:
```
/dev/sda5       /media/d        vfat    rw,user,auto,exec,gid=100,uid=1000,umask
=002,iocharset=utf8,codepage=850  0
```
Thanks by advance for your help to stay on kub

---

### Post by fanatik on 2007-03-29
look at the man page for mount (in the vfat section), there is an option in there called check= and you can set it to r for relaxed, where upper and lower case are equivalent, or n for normal (default), or s for strict. You might want to try these and see if they help you - I haven't tried them myself.

James.

---

