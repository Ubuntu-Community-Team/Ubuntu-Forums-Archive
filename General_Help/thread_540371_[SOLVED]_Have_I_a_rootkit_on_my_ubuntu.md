---
title: "[SOLVED] Have I a rootkit on my ubuntu ?"
date: 2007-09-01
forum: General Help
---

### Post by bob-linux-user on 2007-09-01
My computer dual boots Windows XP and Ubuntu Feisty.I have installed software for Windows
to read the Linux partitions

On a routine run of AVG anti-rootkit in XP it said that there were two hidden files :

u:\usr\src\linux-headers-2.6.20-15-generic\include\config\w1\con
u:\usr\src\linux-headers-2.6.20-16-generic\include\config\w1\con

I rebooted into Ubuntu, installed rkhunter and ran it.It said

Please inspect:
/dev/.static (directory)
/dev/.udev (directory)
/dev/.initramfs (directory)

What am I looking for and how do I find it ? Is it likely I have rootkits in any of the places suggested by AVG or rkhunter?

Please can someone advise?

---

### Post by rsambuca on 2007-09-01
The two 'con' files aren't rootkits of any kind.  I have no idea what rkhunter is looking at in those other folders, but I would be extremely surprised if you had a rootkit on your linux partition.

---

### Post by Seisen on 2007-09-01
Those files are hidden all the time hence why they came up as being hidden. Also here is one thing that rkhunter does look for

> Look for hidden files

---

### Post by david_2001 on 2007-09-01
> **bob-linux-user said:**
> My computer dual boots Windows XP and Ubuntu Feisty.I have installed software for Windows
to read the Linux partitions

On a routine run of AVG anti-rootkit in XP it said that there were two hidden files :

u:\usr\src\linux-headers-2.6.20-15-generic\include\config\w1\con
u:\usr\src\linux-headers-2.6.20-16-generic\include\config\w1\con

There will be a con.h file in those two directories, each of which should be an empty text file, but there shouldn't be a file called just "con" in either.  Even if those con files are there, they aren't hidden because the filename doesn't start with a dot (so .con would be a hidden con).  Even if they are there and hidden, if they aren't executable then they shouldn't be an immediate cause for concern.
> I rebooted into Ubuntu, installed rkhunter and ran it.It said

Please inspect:
/dev/.static (directory)
/dev/.udev (directory)
/dev/.initramfs (directory)

What am I looking for and how do I find it ? Is it likely I have rootkits in any of the places suggested by AVG or rkhunter?

Please can someone advise?

One of the things that rootkit hunters do is build a database of all the files stored on a computer and then look for changes over time.  The contents of those /dev directories will change regularly in the normal course of events, e.g. each time your computer is booted or if a peripheral device is switched on or off.

---

### Post by bob-linux-user on 2007-09-02
Thanks to all that replied-it has put my mind at rest.

Regards

Bob

---

