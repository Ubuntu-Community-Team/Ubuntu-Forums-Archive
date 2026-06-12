---
title: "Dual Boot XP + Ubuntu help"
date: 2007-04-17
forum: General Help
---

### Post by groovdafied on 2007-04-17
I already have one 180 gig hard drive r with  3 partitions made.

1.) ext3 100G Primary
Extended
-Logical 1: Swap space  5g
-Logical 2: Fat32

Well during the installation, it didn't format that last logical drive so I can install xp on it. So I run the CD, and it finds the partitions, but won format it. I tried deleting the logical drive, but it wiped out my whole hard drive and I had to do it again.

So in ubuntu, how can I find the Logical drive, format it as FAT32 so xp will install in it?

I appreciate your help.

---

### Post by kornhead127 on 2007-04-17
Whoa, first of all Microsoft likes to think Windows is the only operating system out there, so you will need to install it first. Your partitions should also look more like this...

1. [Windows ???GB NTFS]
2. [Linux ???GB EXT3]
3. [Linux-Swap 1 or 2 GB linux-swap]

Fill in your partition sizes. Your swap doesn't have to be that big. One gigabte is perfect. The partitions are all primary not logical! 
Install Windows first because it will overwrite the master-boot-record (mbr). Next install Ubuntu to the second partition and point the swap to the third. Install grub to mbr, which is default, and everything should be fine.

NOTE: If at all possible, set up the partitions on the Ubuntu live cd, and format the NTFS partition with the Windows CD. Ubuntu has problems formatting for NTFS, don't risk it. Also don't even think about installing Windows on FAT32, NTFS is much more advanced and will speed up seek times.

Hope this helps. Good Luck!

Oh yeah one minor note

got to a terminal and type

```
gksu gedit /boot/grub/menu.lst
```

Scroll down until you get to the list of operating systems and add this

```
title Windows XP
rootnoverify (hd0,0)
makeactive
chainloader +1
```

As you can probably tell this will allow you to boot Windows with grub.

Ok now have fun.

---

### Post by groovdafied on 2007-04-17
(sigh)....thanks for the help....I'm very new to linux and alwayss were around windows. As for fat32, I had it at that, so windows would install it's "necessary files" when I  run the installation from the CD

---

### Post by Naatan on 2007-04-17
it's propably easier to install windows first and then ubuntu, as ubuntu is friendlier to windows than windows is to ubuntu..

either way, why in the world do you want to use fat32? Not to say NTFS is oh-so-great but it beats FAT32.. if your gonna install windows, install it on NTFS..

and to get it formatted right, boot up from your cd-rom, when it asks you where to install windows select the fat32 disk and click D to delete it, then select L to confirm, after that create a new partition out of the unused/free space available on the disk and format it as NTFS..

You'll most propably end up with a windows boot screen though, and no more grub

---

### Post by kornhead127 on 2007-04-17
Follow the steps I provided and you should be set up and running in no time. Don't be afraid of it it's not all that hard. Print out my post or something and follow the steps.

---

### Post by bagadonitz on 2007-04-21
I got a question on this one.

I have been through this exactly as described 5 times today.  I've read every guide I coudl find, still no go.

At the last steps of the installation when it installs grub, it finds my windows xp 64 bit, I tell it to go ahead and do it up with grub, it finishes, reboot and I get "Error loading operating system error" or <Windows root>/system32/ntoskrnl.exe corrupted error.

I've reinstalled xp, I'm used the recovery console to recover that tile, I've done it all to no avail.  Can't boot XP or Ubuntu.  There is no sign that grub ever even offers to try and start, let alone give me an option on which one to choose.

I've given up on XP now as I'm hoping Ubuntu will do everything I need it to but I hate giving up.  I'm going solo ubuntu now to see that I can get my year old, almost full 1.2TB RAID 5 NTFS array to work in Ubuntu but if I need to get back to a windows install, it would be nice to get the dual boot working.  What am I missing.

---

