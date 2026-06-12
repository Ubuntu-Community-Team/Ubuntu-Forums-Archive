---
title: "Cant access dvd drive"
date: 2012-10-21
forum: General Help
---

### Post by rigidigital on 2012-10-21
Why is this.. I can access any usb sticks, infact every perperal I have connected, modems , scanners, printers worked as soon as I had ubuntu up and running.

Ive tried navigating to the CDROM folder, but nothing there ?


If the USB sticks mount automatically, whats going on with the dvd drive ?

Help me :) :KS

---

### Post by Starcruiser322 on 2012-10-21
We need a little more information to help with this. Please post the output from these commands:
lsb_release -c
uname -a
cat /var/log/dmesg | egrep '(CD|DVD)'

The first two tell us your linux version and kernel, the third the currently installed cd/dvd devices

---

### Post by rigidigital on 2012-10-21
I hope this is correct ?

mike@ubuntu:~$ lsb_release -c
Codename:	precise
mike@ubuntu:~$ uname -a
Linux ubuntu 3.2.0-30-generic #48-Ubuntu SMP Fri Aug 24 16:52:48 UTC 2012 x86_64 x86_64 x86_64 GNU/Linux
mike@ubuntu:~$ 
mike@ubuntu:~$ cat /var/log/dmesg | egrep '(CD|DVD)'
[    2.632644] ata2.00: ATAPI: TSSTcorp CDDVDW SH-222AB, SB00, max UDMA/100
[    2.634399] scsi 1:0:0:0: CD-ROM            TSSTcorp CDDVDW SH-222AB  SB00 PQ: 0 ANSI: 5
[    2.636979] cdrom: Uniform CD-ROM driver Revision: 3.20
[    2.637099] sr 1:0:0:0: Attached scsi CD-ROM sr0
mike@ubuntu:~$

---

### Post by Starcruiser322 on 2012-10-21
That rules out a driver problem, it seems to be installed. Have you tried another disk?
The next commands to try will tell us if you can access the drive at all:

wodim --devices   (make a note of the /dev/*, that is your drive mount point)
sudo su                 (become root)
mkdir /media/cddvd
mount -t iso9660 _/dev/scd0_ /media/cddvd    (replace scd0 if it does not match yours, you should get a read-only warning)

Once these are done, you *should* be able to see the contents of the disk in the /media/cddvd folder you made, unless it is an audio cd.

---

### Post by rigidigital on 2012-10-21
[FONT="Century Gothic"][SIZE="3"]I can now access the dvd no problems. I used another disk. An old one. The one that didnt work was brand new with a couple of files on it.. should not have been a problem. Thanks for the help. I honestly would not have bothered this forum if I thought for a second there could be something wrong with the disk. Sorry about that.[/SIZE][/FONT]

---

### Post by Starcruiser322 on 2012-10-21
It's not a bother, sometimes you just need another person's perspective to solve a problem.
Please mark thread solved if you don't have any other questions. Thread Tools>Mark Thread as Solved

---

