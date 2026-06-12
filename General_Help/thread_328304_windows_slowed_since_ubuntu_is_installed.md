---
title: "windows slowed since ubuntu is installed"
date: 2006-12-30
forum: General Help
---

### Post by bigbang on 2006-12-30
i have just installed linux today (successfully), i did this by removing my windows hard drive, inserting livecd, installing ubuntu, reinserting windows disk and editing  the GRUB code to show windows in the menu too. this means that linux and GRUB are on hda and windows is on hdb.

everything up to this point has gone fine that is until we tried to start up windows wich, yes it does load, but so increadbly slowly and it continues to run like this. my uncle say that it is acting as if it doesn't have any ram and im really stuck for ideas on what it could be.](*,) 
here are the results for the fdisk -l:

>>Disk /dev/hda: 10.0 GB, 10005037056 bytes
>>255 heads, 63 sectors/track, 1216 cylinders
>>Units = cylinders of 16065 * 512 = 8225280 bytes
>>
>>   Device Boot      Start         End      Blocks   Id  System
>>/dev/hda1   *           1        1162     9333733+  83  Linux
>>/dev/hda2            1163        1216      433755    5  Extended
>>/dev/hda5            1163        1216      433723+  82  Linux swap / Solaris
>>
>>Disk /dev/hdb: 40.0 GB, 40020664320 bytes
>>255 heads, 63 sectors/track, 4865 cylinders
>>Units = cylinders of 16065 * 512 = 8225280 bytes

>>   Device Boot      Start         End      Blocks   Id  System
>>/dev/hdb1   *           1        4865    39078081    c  W95 FAT32 (LBA)

if you need any more info please just ask.

---

### Post by vazzeroni on 2006-12-30
Does Windows still report the correct amount of RAM? Does it still do this if you remove the linux hard drive? Are you running Windows from the same hard drive in the same place on the chain you were before? What version of Windows?

---

### Post by dcstar on 2006-12-30
> **vazzeroni said:**
> Does Windows still report the correct amount of RAM? Does it still do this if you remove the linux hard drive? Are you running Windows from the same hard drive in the same place on the chain you were before? What version of Windows?

As the file shows, it's W95 (or W98 ) and it is probably continually trying to access the first hard disk that Ubuntu is now on, but being an early version of Windows it isn't smart enough to understand (and ignore) the change.

Best thing might be to put the Windows HD back where it was, install the Linux HD as an additional one and do the install again, Ubuntu won't affect the Windows install (as long as you are careful) and it should all work a lot better if you let it set itself up this way.

---

### Post by bigbang on 2006-12-31
dcstar, last time i tried to install linux on the second disk GRUB wouldn't let either of them load and instead gave me an error 21. so to fix that i had to rewrite the mbr. my windows version is actual win 2k nt so i dont know why linux says its 95 or 98. 
ps. if any one could tell me where i could find tutorials for permanant mount i would like to know because in my list of drives i cant find it and have to mount (manualy) every time i want files from win hard drive.

---

### Post by landcross12 on 2006-12-31
This should work for you... change the entries 'hdb1 to hdb1' to the windows drive and partiton that you want to read.

With you problem with Windows  running slow check to see where Windows is looking for the swap partition, you may need to change this setting if you have insufficent Ram


To Mount windows

You should be able to mount the drive on boot by following these instructions...

Make a new folder or directory
Code:

sudo mkdir /media/windows

Backup your fstab (good practice)
Code:

sudo cp /etc/fstab /etc/fstab_backup

Open up the orginal fstab in gedit
Code:

gksudo gedit /etc/fstab

Assuming the locations of the partion is /dev/hdb1
Add this line to the end of it
Code:
/dev/hdb1 /media/windows vfat iocharset=utf8,umask=000 0 0
Save the file.
Then remount /etc/fstab without rebooting
Code:

sudo mount -a

---

### Post by bigbang on 2007-01-01
landcross12, im not sure i understand the first two paragraphs you posted could you please explain in more detail. 
also, new development; i found that even if i put windows back as the master it wouldn't run any faster with linux still in the system. this is funny because last time i installed and had to rewrite the MBR for windows i managed to run windows fine (with linux as slave) to reformat the linux disk. this leads me to belive GRUB is the problem here.
any ideas?](*,)

---

### Post by bigbang on 2007-01-11
Thank you every one who replied even if in the end it didn&#8217;t help me find the answer (at least you tried:KS ).
The fix is very simple and I don&#8217;t know why I didn't find it earlier. The problem was that windoze (I use the term for the first time!) didn&#8217;t use the bios to find all the drives but looked through its list of drivers. This meant that I would find the drive if I disabled the drive thought the bios or though grub. So in the end all I had to was disable the drive through windows devise manger (doing it its own way[-( tch,tch!). so if anyone is helped by this I'm glad I posted this reply

---

