---
title: "Gparted unable to shrink ntfs partition and crashes"
date: 2020-06-16
forum: General Help
---

### Post by badidrox on 2020-06-16
I have been trying to shrink a partition I have from 580gb to 450gb. I get the following error when I use gparted as usual:
   [TABLE]
[TR]
[TD="colspan: 2"]**Shrink /dev/sda3 from 564.81 GiB to 439.81 GiB**  00:00:25    ( ERROR ) [/TD]
[/TR]
[TR]
[TD]    [/TD]
[TD] [TABLE]
 [TR]
 [TD="colspan: 2"] calibrate /dev/sda3  00:00:00    ( SUCCESS ) [/TD]
 [/TR]
 [TR]
 [TD]    [/TD]
 [TD] [TABLE]
 [TR]
 [TD="colspan: 2"] [I]path: /dev/sda3 (partition)
start: 493701120
end: 1678202879
size: 1184501760 (564.81 GiB)[/I] [/TD]
 [/TR]
 [/TABLE]
 [/TD]
 [/TR]
 [/TABLE]
 [TABLE]
 [TR]
 [TD="colspan: 2"] check file system on /dev/sda3 for errors and (if possible) fix them  00:00:25    ( ERROR ) [/TD]
 [/TR]
 [TR]
 [TD]    [/TD]
 [TD] [TABLE]
 [TR]
 [TD="colspan: 2"] ***ntfsresize -i -f -v '/dev/sda3'***  00:00:25    ( ERROR ) 



[/TD]
[/TR]
[/TABLE]
[/TD]
[/TR]
[/TABLE]
[/TD]
[/TR]
[/TABLE]

---

### Post by dino99 on 2020-06-16
Main rule is: use windows tool with windows (aka ntfs partition), use linux tool with linux  ):P

---

### Post by TheFu on 2020-06-16
use ms-windows to fix the file system errors.  While you have Windows booted, just resize it there. Best to close the file system in Windows before disconnecting or shutting down the system.  MSFT doesn't always close file systems when a computer is shutdown. There are settings inside MS-Windows to control that.

Addtionally, gparted won't handle non-simple file systems. NTFS has multiple non-simple modes.

---

### Post by badidrox on 2020-06-16
what can I do if i don t have windows. I have already shrinked multiple ntfs partitions using gparted before. I tried to shrink the same partition using a live usb and the same problem occured.

---

### Post by TheFu on 2020-06-16
Phone a friend and take your HDD to that friend to fix NTFS.
Why have NTFS if you don't have Windows? There are a few valid reasons.  When my only NTFS portable USB storage gets corrupted, i reformat it and start fresh.  it doesn't hold any long-term data, usually just on there for 10 hrs max.

---

### Post by badidrox on 2020-06-16
still not a solution to the main problem , as i said , its supposed to work as it worked before. there is no reason for it to not work as it did before.

---

### Post by ActionParsnip on 2020-06-16
Did you run a chkdsk on the NTFS to make sure it is consistent before you started manipulating it?

---

### Post by badidrox on 2020-06-16
no i will try asap

---

### Post by CelticWarrior on 2020-06-16
FYI, chkdsk is a Windows tool. Again, you need Windows tools to correct NTFS errors. GParted can easily resize NTFS partitions provided there are no errors or the drive isn't hibernated due to the Fast Startup feature being the default in any Windows 8 or newer.

NTFS can't be error corrected in Linux and that's why having such partitions without an installed Windows at hand is really a very bad idea.

---

### Post by badidrox on 2020-06-16
which means if an error happend while using gparted to resize then u cant fix it using linux and only using a windows device ? okay i will try to find one. what commands should i use ? chdsk would show what ?

---

### Post by CelticWarrior on 2020-06-16
Yes, except the error didn't happen while using gparted, the error was there before and was detected by gparted that in turn refused to mess with that partition in order to avoid further problems.

---

### Post by ActionParsnip on 2020-06-16
right click each drive in turn and click properties. Tools tab and "check the drive for file system errors". Do this on all NTFS partitions. Have you never had to do this? Seems weird.

---

### Post by TheFu on 2020-06-16
> **badidrox said:**
> still not a solution to the main problem , as i said , its supposed to work as it worked before. there is no reason for it to not work as it did before.

Your belief there isn't any problem doesn't make it so. I have a similar problem sometimes with my beliefs. ;) I'll insert my world view regardless of reality.  gparted isn't out to get you. I promise.

The software on Linux has found something that doesn't seem right and decided rather than trash all the data, it would refuse to attempt the request. Count yourself lucky. Total data loss would be the alternative.

If you like, you can manually run the 
```
ntfsresize -i -f  [--size SIZE[k|M|G]] -v /dev/sda3 
```
command. There are lots of options in the manpage for that command.

There are a few KNOWN ISSUES listed in the manpage. They recommend reading the "Ntfsresize FAQ" too. 

As others have said, gparted just saw something it couldn't handle and decided not to attempt what you requested.  That "something" wasn't caused by gparted, but by something else.  ntfsresize doesn't touch the partition table according to the manpage.  Something did something to leave the partition or file system in a state where touching that file system would likely be very bad.  We've listed some of those things.

**chkdsk** is a Windows file system validation and correction tool. It works from inside MS-Windows. A newer tool, **scandisk** does similar, but different checks. This is also an MS-Windows tool. Both were created by MSFT, so they have native access to the internal structures with complete understanding, not reverse engineered access like Linux uses.

But if you don't have Windows, why do you want NTFS at all?  I'm confused.

---

