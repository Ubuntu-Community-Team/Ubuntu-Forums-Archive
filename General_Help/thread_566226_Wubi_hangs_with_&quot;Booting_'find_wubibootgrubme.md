---
title: "Wubi hangs with &quot;Booting 'find /wubi/boot/grub/menu.lst'&quot;"
date: 2007-10-03
forum: General Help
---

### Post by ClausG on 2007-10-03
Hello,

I installed Wubi 7.04.04 on the first partition (NTFS) auf my **second** hard disk. When booting Wubi hangs with "Booting 'find /wubi/boot/grub/menu.lst'". If I install Wubi on the first partition of my **first** hard drive everything works fine. On my computer at work I have Wubi installed on second partion of first hard disk and this works wonderful. My son has the same constellation (second partition on first HD) and it works fine, too.
 
All I could find in the forum were problems with Vista and SATA, but I use XP und my HDs are IDE. Any ideas?

Claus

---

### Post by abhilash82 on 2007-10-03
There are different reasons why wubi doesn't work. 

1. If you hard reboot, the filesystem can get corrupted. In this case you need to run chkdsk /r
2. Grub issues. Check #1 first. Make sure that your boot files look right (boot.ini in XP). Make sure that the wubi files are in place. You can press ins rapidly at the beginning of the bootloader then run the commands manually to check the error (type help).
3. Defrag the partition where you have your Wubi installed.
4. If your partition is NTFS, then check whether it is compressed. Uncompress the whole partition.

---

### Post by ClausG on 2007-10-04
My partition is not compressed and has not get corrupted and I defragmened it. No changes.

Every partition has a wubildr an wubildr.mbr. Here's my boot.ini:

[INDENT] [FONT="Courier New"][boot loader]
timeout=15
default=multi(0)disk(0)rdisk(0)partition(1)\WINDOWS
[operating systems]
multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Microsoft Windows XP Professional" /fastdetect /NoExecute=OptIn
c:\wubildr.mbr="Ubuntu"
[/FONT][/INDENT]

I wonder why there is c:\wubildr.mbr. Shouldn't it be D: if I install on this partition?

Claus

---

### Post by ClausG on 2007-10-04
I don't know why there is "WINDOW S" instead of "WINDOWS" and "Micro soft" instead of "Microsoft". There aren't these blank characters in my boot.ini and in my posting befere I sent it.

Claus

---

### Post by ago on 2007-10-04
> **ClausG said:**
> 

I wonder why there is c:\wubildr.mbr. Shouldn't it be D: if I install on this partition?

Claus

C: is fine but wubildr.mbr is weird that is only used for vista...
Edit: forget that

---

### Post by ClausG on 2007-10-05
What do you mean by "Edit: forget that"? If I wipe out the line 'c:\wubildr.mbr="Ubuntu"' I wouldn't have a start menu, I think. On my PC at work (XP, too), where Wubi was installed on 2nd Partition of 1st HD the line is the same. 

Claus

---

### Post by ago on 2007-10-05
> **ClausG said:**
> What do you mean by "Edit: forget that"?
wubildr.mbr is fine

Do you have /wubi/boot/grub/menu.lst?

---

### Post by ClausG on 2007-10-05
Yes, I see a file D:\wubi\boot\grub\menu.lst

It contains (lines starting with # left out):

[FONT="Fixedsys"]default        0
timeout        1
hiddenmenu

title Ubuntu
find --set-root --ignore-floppies /wubi/boot/linux
kernel /wubi/boot/linux find=/wubi/boot/linux quiet ro
initrd /wubi/boot/initrd
boot

### END DEBIAN AUTOMAGIC KERNELS LIST

title Ubuntu (Original Kernel)
find --set-root --ignore-floppies /wubi/boot/linux
kernel /wubi/boot/linux find=/wubi/boot/linux setup_iso=ubuntu-7.04-alternate-i386.iso quiet splash ro
initrd /wubi/boot/initrd
boot[/FONT]

Claus

---

### Post by ClausG on 2007-10-14
No more ideas?

Claus

---

### Post by ago on 2007-10-15
Claus new wubi version will contain a brand new grub4dos, you might want to try that.

---

### Post by ClausG on 2007-10-15
Okay ago, 

must I wait some days? (how many?) Or can I download the newer version today? On [http://www.wubi-installer.org/](http://www.wubi-installer.org/) I only found 7.04.04.

Claus

---

### Post by ago on 2007-10-15
[http://wubi-installer.org/devel/minefields/](http://wubi-installer.org/devel/minefields/)

Couple of caveats, uninstall any previous wubi installation 
The installer will crash in some circumstances (it should not have any external impact), in case try again, and if it fails you'll have to wait for a fix.
The ISO needed is the DESKTOP release candidate.

---

### Post by ClausG on 2007-10-25
Hi Ago,

I had some troubles with older alphas but with Wubi-7.10-alpha-rev368.exe I got it working.

You've done a good job!
Claus

---

### Post by pappuks on 2007-10-26
I also had the same problem. I solved it be booting into windows and running chkdsk on the partition where wubi was installed, i.e. d: drive.

chkdsk found some error with the disk and it fixed it. It created a found.000 hidden folder in d: in which it had moved my wubi folder.

I just copy pasted the folder inside folder.000 (can't remember the name) to d: and renamed to wubi.

After restart Ubuntu started working fine.

Hope that this information helps.

Kuldeep.

---

### Post by mercedesj on 2008-02-16
Hello,

I've the same problem that ClausG.
I installed Wubi 7.10  on  my second hard disk. When booting Wubi hangs with "Booting 'find ubuntu/install/boot/grub/menu.lst'" Error 17: file not found.  I use XP. Any ideas?

Mercedes

---

