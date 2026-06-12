---
title: "Hesitation to switch to Ubuntu"
date: 2006-11-01
forum: General Help
---

### Post by Aquiva on 2006-11-01
Hola, I absolutely love Ubuntu and I really want to switch, but I have a few questions...

-Startup:
After I've installed Ubuntu, is their still a way I can boot Windows instead at startup? (like by pressing and holding "W" while booting?) ... And being able to access all the same files that I originally could?

-Applications:
I have several (paid for) software on Windows... Adobe, Corel, Vegas. I still want to be able to use them. Is there a way I can install them / run them on Ubuntu - even though they are Windows installs?

-Drivers:
When I plug things into the computer (like my camera's SD chip) will it be able to access the files and all?
Will my other hardware work? Like my Logitech mouse' extra button functions? Printing. etc.? (Will I have to reinstall them? Or will they auto-work. Will the Windows installs even work?)

-Networking:
We have two main computers, my brother is still using Windows and likely won't be switching anytime soon. Will I be able to access files from his computer across the LAN and everything?

Thanks!
I'm not code-geeky, but I am computer-geeky. And since I am brand new to Linux and Ubuntu... please treat me as an imbecile :P - cause I won't know how to do some things or know what you are referring to.

*really wanting to switch to Linux,*
 ~ Mark

---

### Post by aysiu on 2006-11-01
There's something called a "dual-boot," which allows you to choose at start-up which OS you want to boot into (just press the up and down arrows). Ubuntu will be the default, but you can change Windows to the default, too, if you share a computer with Windows users.

You can see the dual-boot setup process here:
[http://www.psychocats.net/ubuntu/installing](http://www.psychocats.net/ubuntu/installing)

It's always a good idea to use native Linux programs whenever possible. However, there are some helper programs that allow you to run many (but not all) Windows programs within Ubuntu--Wine, Crossover Office, and Cedega.

Ubuntu should recognize most hardware, with some exceptions. There are hardware compatibility lists available, but you can also run the Desktop CD (or "live CD") without affecting your hard drive. This runs a usable Ubuntu session from the CD and your computer's RAM, and you get a no-commitment test drive of Ubuntu... and its hardware detection.

---

### Post by theicyj on 2006-11-01
> -Applications:
I have several (paid for) software on Windows... Adobe, Corel, Vegas. I still want to be able to use them. Is there a way I can install them / run them on Ubuntu - even though they are Windows installs?
- I had the same problem with a few engineering apps I use that are not available for Linux (yet), I would recommend VMware.  I never had much luck with Crossover Office.  [Check out this great how-to for setting up VMWare.]("http://ubuntuforums.org/showthread.php?t=183209")

> -Drivers:
When I plug things into the computer (like my camera's SD chip) will it be able to access the files and all?
Will my other hardware work? Like my Logitech mouse' extra button functions? Printing. etc.? (Will I have to reinstall them? Or will they auto-work. Will the Windows installs even work?)
-  I switched to Ubuntu three months ago, and I love the "out of the box" hardware support.  You normally don't have to install drivers for all your devices like in windows, cutting back significantly on set-up time.  My wireless Logitech multimedia keyboard and mouse just work! Same with my HP printer, Saitek gamepads, and digital camera!  I did have some problems with my Lexmark all-in-one though.

> -Networking:
We have two main computers, my brother is still using Windows and likely won't be switching anytime soon. Will I be able to access files from his computer across the LAN and everything?
- You will still be able to access windows shares, or share folders for access from a windows machine with samba.  It is fairly easy to set up too.

---

### Post by Aquiva on 2006-11-01
Alright, I went ahead and Installed Ubuntu (because I can still revert back to Windows through GRUB if necessary).

But I want to be able to access all my files from Windows (You know how it goes, D: partition is all Window's local operating junk. However **C:** is where all your files are stored)

How do I get Ubuntu to be aware of C: and access the files? (For instance, open .doc, .jpegs, etc. common files that Ubuntu can already import/access)

I'll be asking a bunch of questions as I come across things. Thanks for the great support :).

 ~ Mark

---

### Post by LenzM on 2006-11-01
A great guide if you are comfortable (or want to get comfortable) with the command line is here: 
[http://ubuntuguide.org/wiki/Ubuntu_Edgy](http://ubuntuguide.org/wiki/Ubuntu_Edgy)

Specifically for mounting Windows partitions:
[http://ubuntuguide.org/wiki/Ubuntu_Edgy#Windows](http://ubuntuguide.org/wiki/Ubuntu_Edgy#Windows)

---

### Post by clickwir on 2006-11-01
> **Aquiva said:**
> Alright, I went ahead and Installed Ubuntu (because I can still revert back to Windows through GRUB if necessary).

But I want to be able to access all my files from Windows (You know how it goes, D: partition is all Window's local operating junk. However **C:** is where all your files are stored)

How do I get Ubuntu to be aware of C: and access the files? (For instance, open .doc, .jpegs, etc. common files that Ubuntu can already import/access)

Unless you installed things bass backwards on purpose, your windows system files will be on C: and other things on D:. 

Linux doesn't use drive letters. Your windows partitions will probably be already be mounted for you under /media/hda1 and /media/hda2. You'll need to check out what's in each to figure out which is which for your C:/D: backwardsness.

But yes, linux can read windows files just fine.

---

### Post by aysiu on 2006-11-01
> **Aquiva said:**
> Alright, I went ahead and Installed Ubuntu (because I can still revert back to Windows through GRUB if necessary).

But I want to be able to access all my files from Windows (You know how it goes, D: partition is all Window's local operating junk. However **C:** is where all your files are stored)

How do I get Ubuntu to be aware of C: and access the files? (For instance, open .doc, .jpegs, etc. common files that Ubuntu can already import/access)

I'll be asking a bunch of questions as I come across things. Thanks for the great support :).

 ~ Mark
Follow these directions:
[http://www.psychocats.net/ubuntu/mountwindows](http://www.psychocats.net/ubuntu/mountwindows)

---

### Post by Aquiva on 2006-11-03
Thanks. I followed them, but got lost once I got to the sudo nano. I don't know what exactly to edit.

Here is the fdisk -l command:
Device Boot           Start             End           Blocks     id    System
/dev/sda1 *            579           13948         107394525      7 HPFS/NTFS
/dev/sda2              ............
(goes till /dev/sda5. W95 FAT32, Linux, Extended, Linux swap / Solaris.)

Partition table entries are not in disk order

disk /dev/sdb: 1023 MB, 1023934464 bytes
2 heads, 32 sectors/track, 31248 cylinders
Units = cylinders of 64 * 512 = 32766 bytes

Device Boot        start          end          blocks         Id     system
/dev/sdb1 *            1        31247          999888          6     FAT16


I also created a /windows folder.
So how do I mount the /dev/sda1 (which I assume is the folder with my regular files) to /windows ? or whatever?

Do I have to do all the sudo nano edit?

thanks :)

(p.s., how do I make it so my panel with my windows doesn't auto-clump the programs? Cause I dislike having to click on GAIM window, then click on which window I want. thanks!)

 ~ Mark

---

### Post by hyper7 on 2006-11-03
This is rather good if you want to read/write to NTFS..
[http://www.arsgeek.com/?p=675#more-675]("http://www.arsgeek.com/?p=675#more-675")

> Do I have to do all the sudo nano edit?[QUOTE][/QUOTE]

You can replace nano with gedit if it's easier for you to understand.

I couldn't understand your last question.  Sorry.

---

### Post by LenzM on 2006-11-03
> **Aquiva said:**
> 
(p.s., how do I make it so my panel with my windows doesn't auto-clump the programs? Cause I dislike having to click on GAIM window, then click on which window I want. thanks!)

 ~ Mark

I think this is what you're refering to:
Right click on the bottom left of the panel (where the very faint dots are) and choose preferences.  Then change window grouping to never or when space is limited.

---

### Post by Aquiva on 2006-11-03
Thanks LenzM! I got it. 

I've tried to follow the tutorials, but I still can't modify them correctly to fit my system. But I don't know what to do :/.
There isn't something I can install that will auto-detect my windows partition, and then modify things accordingly?
Or, what kind of information do I need to C&P (speaking of which, how do I C&P things from the terminal?) information so you guys can help me figure it out?

 ~ Mark (local linux illiterate)

---

### Post by LenzM on 2006-11-03
run the following two commands and post the results, after that I should be able to tell you exactly how to get this working.
```

df -h
cat /etc/fstab

```

---

### Post by Aquiva on 2006-11-03
```
mark@Aquiva:~$ df -h
Filesystem            Size  Used Avail Use% Mounted on
/dev/sda3              76G  1.9G   70G   3% /
varrun                501M   80K  501M   1% /var/run
varlock               501M     0  501M   0% /var/lock
procbususb             10M  152K  9.9M   2% /proc/bus/usb
udev                   10M  152K  9.9M   2% /dev
devshm                501M     0  501M   0% /dev/shm
lrm                   501M   18M  484M   4% /lib/modules/2.6.17-10-generic/volatile
/dev/sdb1             977M   29M  949M   3% /media/usbdisk
/dev/hda              405M  405M     0 100% /media/cdrom0
mark@Aquiva:~$ cat /etc/fstab
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda3
UUID=ee32bebb-c3bd-4090-b191-0b5acea6201e /               ext3    defaults,errors=remount-ro 0       1
# /dev/sda5
UUID=b8d8ccab-0c10-4c59-b0a6-4f955c756929 none            swap    sw              0       0
/dev/hda        /media/cdrom0   udf,iso9660 user,noauto     0       0

```

In addition, here is the fdisk -l command:
```
Disk /dev/sda: 200.0 GB, 200049647616 bytes
255 heads, 63 sectors/track, 24321 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *         579       13948   107394525    7  HPFS/NTFS
/dev/sda2               1         578     4642753+   b  W95 FAT32
/dev/sda3           13949       23947    80316967+  83  Linux
/dev/sda4           23948       24321     3004155    5  Extended
/dev/sda5           23948       24321     3004123+  82  Linux swap / Solaris

Partition table entries are not in disk order

Disk /dev/sdb: 1023 MB, 1023934464 bytes
2 heads, 32 sectors/track, 31248 cylinders
Units = cylinders of 64 * 512 = 32768 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1       31247      999888    6  FAT16

```

Thank you so much :).

 ~ Mark

---

### Post by LenzM on 2006-11-03
(You read my mind, I meant to ask you to print the fsdisk too.)

```

sudo mkdir /media/windows
gksudo gedit /etc/fstab

```

add the following line

```

/dev/sda1       /media/windows  ntfs    umask=0222      0       0

```

now run
```

sudo mount -a

```
and the drive should be mounted in /media/windows
When you restart I think an icon will appear on your desktop.  This mounted it in read-only since there's a chance that linux can screw up ntfs partition when writing, so you won't be able to change anything on there.

---

### Post by Aquiva on 2006-11-04
It worked! Wow! **Thank you.** Amazingly much.

Two final questions on the issue of Windows mounting:
-Will Windows OS still be able to access all of its files?
-If I want to dare Linux, what do I edit to make the mount writable? "unmask=0000"?

Thanks :) (you guys rock)

 ~ Mark

---

### Post by bionnaki on 2006-11-04
yes, dual-booting/mounting a windows partition will not affect the Windows OS ability to access the files.

you can only read files on ntfs from linux. in order to read/write from linux, the windows partition has to be fat32. I think there are ways to read/write on ntfs, but I am not sure how stable it is yet. When I dual-booted (deleted the windows partition after a month because I never used it anymore) I simply would copy the files on my windows partition over to my linux partition so I could write. Try that.

---

### Post by Aquiva on 2006-11-04
Oh right, that is an obvious solution. sudo mkdir /home/mark/files
sudo cp /media/windows /home/mark/files
And then should I dismount /media/windows ?

Alrighty, new issues (thanks all for helping out):
1. Crossing Over.
VMplayer doesn't install because the etc/init.d path won't allow it to copy files to that location. How do I make VMplayer install completely? (Note: this is going off of the original link givin me.)
On Windows I got VMplayer to run ubuntu, however it was too slow. But how does Ubuntu to Windows work? Do I need an .iso of Windows?

Alternatively I can get Wine.
However, the Wine installation/download confused me (I couldn't find out how to "add" a new SPM - is this because I'm on 6.10, and Wine is only for 6.06?). 
How can I get Wine downloaded/installed/running on 6.10?

2. Networking
Somebody suggested Samba, so I downloaded the latest release... but under terminal install I got this error:
./autogen.sh: need autoconf 2.53 or later to build samba from SVN
**shrug**?

3. Random:
How do I get all the usual plugins for Totem?
Is VLC player or others better than Totem?
If so, how do I install them? The Add/remove program says I can't because I have a conflicting software. It says to switch to advance - sorry to be newby, how do I get to advance? And once I do, how do I know what to remove so VLC player can be downloaded and installed?

Thanks :)

 ~ Mark

---

### Post by Aquiva on 2006-11-04
Is the reason why I'm having a lot of these problems because they applications aren't built for 6.10 but 6.06?

 ~ Mark

---

### Post by LenzM on 2006-11-05
Not sure about vmware and wine, but I think Totem is as good as any of the alternatives.  The easiest way to get plugins and some other really useful stuff is to use automatix, go to [www.getautomatix.com](www.getautomatix.com)

---

