---
title: "grub not loading"
date: 2007-03-02
forum: General Help
---

### Post by djork on 2007-03-02
hi,
total newb here
can someone please help?
i have a dual boot set up at the moment with xp and ubuntu.with partitions on two sata hard drives(both os's are ont the first hard drive).anyways my problem lies with my boot up, it hangs on verifyng dmi pool...or something like that.it doesnt get to my grub boot list unless i put in the ubuntu dapper disc and choose the option boot from first hard disc(only if i change bios to boot cd first ofcourse).then everything loads fine i even get my options of which os i would like to boot.how do i fix this so my grub starts up again?what do i fix?and how!thanks again.

---

### Post by chewearn on 2007-03-02
hi, can you post output of
```
sudo fdisk -l
```

---

### Post by djork on 2007-03-03
will do, i havent had a chance to get to my computer.i will do it tonight..aussie time...in a few hours.

---

### Post by djork on 2007-03-04
Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        3824    30716248+   7  HPFS/NTFS
/dev/sda2            3825        8923    40957717+  83  Linux
/dev/sda3            8924       19457    84614355    5  Extended
/dev/sda5           14024       19122    40957686    7  HPFS/NTFS
/dev/sda6           19123       19457     2690856   82  Linux swap / Solaris
/dev/sda7            8924       14023    40965687   83  Linux

Partition table entries are not in disk order

Disk /dev/sdb: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1        7649    61440561    7  HPFS/NTFS
/dev/sdb2            7650       15298    61440592+   7  HPFS/NTFS
/dev/sdb3           15299       22947    61440592+   7  HPFS/NTFS
/dev/sdb4           22948       30401    59874255   83  Linux

---

### Post by chewearn on 2007-03-04
Ok, not sure this will help; I don't have a similar dual boot system to test it.  But...

I see the boot flag on your XP partition; try changing that to your linux partition.

---

### Post by djork on 2007-03-04
newbie here..how do u do that?

---

### Post by chewearn on 2007-03-04
Boot into the LiveCD, go to System -> Administration -> Gnome Partition Editor

Right-click on you Linux partition, select Manage Flags; then select checkbox next to Boot.

---

### Post by djork on 2007-03-04
i have the gnome partition editor on my system-which i can still boot into using the cd but i dont get the option to manage flags.if i boot into the cd rather than my hard drive will i get this new option?

---

### Post by chewearn on 2007-03-04
That's strange.  I got the option on my system.  How about if you select the linux partition (left-click).  Then, Menu -> Partition; did you see a manage flags item?

---

### Post by djork on 2007-03-06
im using gparted 0.1 is that the same thing?
actually i tried the super grub disc program but i keep getting an error 28 selected item cannot fit into memory,when it tries to load the menu list file(or something similar)any ideas
anyone?

---

### Post by chewearn on 2007-03-07
I have GParted version 0.2.5 on my up-to-date Edgy install.

---

### Post by djork on 2007-03-07
did that error message ring any bells?is the mbr rooted?do i fix the xp mbr and then fix the ubuntu one?i dont know what im talking about...the more forums that i search the more confused i get

---

### Post by chewearn on 2007-03-07
I'm not familiar with super grub disc, don't know about "error 28".  You can try the GParted LiveCD:
[http://gparted.sourceforge.net/livecd.php](http://gparted.sourceforge.net/livecd.php)

> is the mbr rooted?do i fix the xp mbr and then fix the ubuntu one?

Up to now, I have only see the fdisk -l output; this does not tell whether grub is properly installed and set-up.  I thought it might be possible to simply fix the problem by setting the boot flag.  However, you can also try to reinstall grub again.  (there is no need to fix XP MBR; doing so will only screw up everything, as XP does not respect Linux installation).

[http://www.ubuntuforums.org/showthread.php?t=24113&highlight=grub](http://www.ubuntuforums.org/showthread.php?t=24113&highlight=grub)

---

### Post by djork on 2007-03-08
thanks for all ur help so far, by the way.i will give that program a try tonight.till then astala vista!

---

### Post by djork on 2007-03-12
i have no cd's
till i get some i am stuck!

---

### Post by djork on 2007-03-14
i got the boot flag up but still no luck.guess its time to back up and restart.hows edgy eft treating you?

i cant help but think this is an easy fix...oh well

---

### Post by djork on 2007-03-14
by the way, thanks again for ur time

---

### Post by chewearn on 2007-03-14
I have Edgy in two PCs.  Almost no problem at all, just some minor annoyance here and there; some I managed to fix, some I just lived with it.

Anyways, since boot flag don't solved it; you could try reinstall grub.

In terminal:
```
sudo grub
```You will get the grub prompt.
```
find /boot/grub/stage1
```Note down the location.  It might be something like (hd0,1).  Use this location for the next command:
```
root (hd?,?)
```Next command will install grub to the hda MBR:
```
setup (hd0)
```Finally, exit grub prompt:
```
quit
```That should do it.

---

### Post by T27M on 2007-03-15
Hi i have kinda the same problem (i think) i tried to reinstall grub the way you said but after```
 setup (hd0)
```

i get 

Error 23 : Error while parsing number

i dont know what this means, please can someone help

---

### Post by chewearn on 2007-03-15
> **T27M said:**
> Hi i have kinda the same problem (i think) i tried to reinstall grub the way you said but after```
 setup (hd0)
```i get 

Error 23 : Error while parsing number

i dont know what this means, please can someone help

What is your output from:
```
find /boot/grub/stage1
```

---

### Post by T27M on 2007-03-16
well it used to give me (hd1,1) or something but now it says
```
Error 15 : File not found
```

??

---

### Post by chewearn on 2007-03-16
If ```
find /boot/grub/stage1
``` gives (hd1,1), you are supposed to enter ```
root (hd1,1)
``` as the next command.

---

### Post by T27M on 2007-03-16
i dont know what i did but now it gives me (hd1,2) i carry on the rest but when i reboot i get

grub loading
error 21

---

### Post by T27M on 2007-03-16
well i think i foud out why it wont work 

Error 21: means that the selcted disk doesnt exist

is there any way i can change it to the right one ??

---

### Post by chewearn on 2007-03-16
1. How is your HDs arranged?  Example: IDE0 master 160GB, IED0 slave 80GB...  Are the master/slave jumpers correctly placed?
Then, check your BIOS see if all harddisks are detected correctly as you arranged them.

2. Do you have a dual boot to Windows, or do you have single ubuntu?

3. Which harddisk has the ubuntu?

---

### Post by T27M on 2007-03-16
I have one internal IDE 10GB with windows on and a 320GB external usb drive with ubntu on

they are both recognised but even with the external one disconnected i cant boot windows

---

### Post by chewearn on 2007-03-16
> **T27M said:**
> I have one internal IDE 10GB with windows on and a 320GB external usb drive with ubntu on

Ok, booting ubuntu from external usb could be tricky; I have no experience as such, but probably grub is not able to correctly detect.  Have to bow to more experienced people.

> they are both recognised but even with the external one disconnected i cant boot windowsOk, problem is grub is probably now installed in your windows HD mbr, that's why you can't boot into windows.  If you would like to restore the windows mbr:
[http://www.ambience.sk/fdisk-master-boot-record-windows-linux-lilo-fixmbr.php](http://www.ambience.sk/fdisk-master-boot-record-windows-linux-lilo-fixmbr.php)

EDIT:
Ok, I did a search on the forum, found this link
[http://www.pendrivelinux.com/2007/01/25/usb-x-ubuntu-610](http://www.pendrivelinux.com/2007/01/25/usb-x-ubuntu-610)
You should fix the Windows MBR first, then use the makeboot.exe from website to boot from usb.

---

### Post by T27M on 2007-03-16
Thanks ill try that

one more question i was reading the usb boot instructions and i just wondered if the partion size would be 700mb the instructions say type
 ```
+700m
``` 

and should i put this to how ever big i want the partion size to be

---

### Post by chewearn on 2007-03-16
I believe the +700MB simply means 700MB or large, but I'm not 100% positive.  As I have mentioned, I have to prior experience with installing ubuntu on a usb drive (maybe that will be my next project) :)

Having re-read the whole instruction again, I think the website deals specifically with creating a "LiveUSB" type of installation on a small 1GB flash drive; but with an additional partition to store persistent data; it might not be something you want for a semi permanent 320GB usb drive. 

I did a quick search on google, there are a lot more info besides the pendrive link.  Maybe you need to research some more, and find a better instruction.  For example there is this long thread from way back, 2005, still active, most recent post just few days ago.
[http://ubuntuforums.org/showthread.php?t=71567](http://ubuntuforums.org/showthread.php?t=71567)

Good luck, sorry could not be more helpful.

---

### Post by T27M on 2007-03-16
No you helped a lot thanks :) 

i have a look at that thread

---

