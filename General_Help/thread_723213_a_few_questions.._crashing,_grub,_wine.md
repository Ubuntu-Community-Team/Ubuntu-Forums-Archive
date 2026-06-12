---
title: "a few questions.. crashing, grub, wine"
date: 2008-03-13
forum: General Help
---

### Post by Kanaric on 2008-03-13
I've been on the fence for a while with linux going back and forth between windows and this and finally cut ties with windows so i'm still not very knowledgable with linux.

I've been having a few issues that I can't figure out how to fix or dont even know where to start or what to ask since i dont know what its really called.

The first problem is with grub, i get this error 17 which i know how to fix but the other problem with it is that the window is like in this black and white and when I import an image is like 16 colors. PLUS when it starts booting where on other distros it would have a bootsplash that you could press F2 or whatever to see what is loading instead of showing anything it like "disables" the video card or something and sends my monitor into standby until its done and gnome starts. 

One problem for me that i tried fixing and couldn't figure out is with wine. I use this program called ventrilo, teamspeak is not an option for me because everyone i do things with online hates that program. It works perfectly, sound works and everything but the main problem i have is that there is this "hack" or program out there to map a key so that you can use your push to talk without having the window selected. I can't figure out which "device" is my keyboard i have /dev/input/event1 to event5 tried them all and it didn't work. Is there a way to see what device is your keyboard?

My final question is if i'm running a variety of programs switching between windows, closing, opening, etc. for a while any program i will run after a while will refuse to launch. This happened on a few distros i've tried not just ubuntu. Ubuntu tells me that they are "crashing".... if anyone has any tips or ideas i'm open to them. Heres my system specs:

Core2 Q6600
2gb ram
650i Asus Board (P5N-E SLI)
8800 GTS 512MB
Seagate SATA "parallel recording" drive. - using ReiserFS partition

512MB Swap - boot/root on same partition using reiserfs
I installed the nvidia drivers

---

### Post by {BzF}~JOKesTER on 2008-03-13
To Find Out What Device Your Keyboard Is - Open A Terminal

And Type:

lsusb

And Look For Something Like "Logitech Keyboard"

Hope This Helps A Tidbit!!:):)

---

### Post by Kanaric on 2008-03-13
Thanks a bunch, that does help.

I did reinstall and changed to EXT3 and the OS overall is acting much better.

I'm still having grub problems though, now i'm non stop getting error 15 issues here is the information that i'm sure people would need to help:

using hardy alpha-6 btw
> Disk /dev/sda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xcef3e17c

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        9728    78140128+   7  HPFS/NTFS

Disk /dev/sdb: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xdbb6dbb6

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1       14592   117210208+   7  HPFS/NTFS

Disk /dev/sdc: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xb349dd08

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1               1       29649   238155561   83  Linux
/dev/sdc2           29650       30401     6040440    5  Extended
/dev/sdc5           29650       30401     6040408+  82  Linux swap / Solaris


fstab
> # /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/sdc1
UUID=788d2337-4838-4449-9b39-f08e19a7f193 /               ext3    errors=remount-ro 0       1
/dev/sdc5
UUID=bfa65292-baca-4179-830a-6a86c67430c8 none            swap    sw              0       0
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/hdd        /media/cdrom1   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0
I'm using the "guided" install selecting to use the sata hard drive that i'm using. For some strange reason fstab had a # to comment out the two sata drives... i removed that and it had no effect. Also my NTFS drives aren't in there yet I can acces them them and they are mounted already... makes me think that this is the wrong fstab or something strange like that.... it is /etc/fstab



After the reinstall i'm still getting tha "black screen" problem.... the topics on the forums havn't helped me so far.

---

### Post by {BzF}~JOKesTER on 2008-03-14
If You Have Dual Drives - The Reason Your Getting That Error - Is It Tries To Boot From The Other Drive First.

To Change This -Try Going Into Your BIOS And Changing The Boot Order:)


Hope This Helps!!

---

### Post by Kanaric on 2008-03-14
> **{BzF}~JOKesTER said:**
> If You Have Dual Drives - The Reason Your Getting That Error - Is It Tries To Boot From The Other Drive First.

To Change This -Try Going Into Your BIOS And Changing The Boot Order:)


Hope This Helps!!
My bios is kind of non helpful in this situation, i can only set bootorder by type of device.... not individual devices of the same type.

Thats ok, i'd rather have to boot from grub on the CD than use windows.




A problem that still lingers is that I tried a few fixes for the "blank" boot screen and none of them have helped. I turned off quiet and turned on nosplash like someone said and it keeps my monitor from going into standby mode yet noting still shows. 

It boots quickly as well, its not slow like some people have reported when they had this problem. I like to know what goes on when this OS is booting so this **** kind of annoys me.

---

