---
title: "grub stage 1.5 read error"
date: 2007-11-17
forum: General Help
---

### Post by MorbidAngel on 2007-11-17
Just installed Ubuntu 7.04 on my main computer, relatively new to linux, however I have gotten it working on two older systems (with xubutu and puppy linux) and i've been searching for about two weeks for an answer to my problem and have found none.  I installed Ubuntu from the live cd (using it right now) and didn't install grub right the first time, so i went into the terminal and installed it into the right drive, and got "grub loading stage1.5read error" on startup, got frustrated and after a while reinstalled Ubuntu the same way but fixed where grub was installed first time around, same problem.

I get no other errors when starting and no keys on my keyboard get me past it, only thing i can do is press ctrl+alt+backspace and restart


I'm running with XP on another hdd and would like grub to dual boot, but since its on another drive I can always get in through the bios

here's the setup:

SATA 1 - XP
SATA 2 - storage, backup XP install
IDE Master - Storage
IDE Slave - Ubuntu

Some people have said that it's a bios problem, my motherboard is an EVGA nForce4 133-K8-NF41-AX SLI, and i've had no problems with it yet, i tried a floppy upgrade but it gave me some floppy error message and gave up, it's only a year old.

---

### Post by meierfra on 2007-11-17
I believed that  you just need to reinstall grub and edit menu.lst. Try the following:


Boot from the Ubuntu LiveCD.  Open a terminal 
and type

```
sudo grub
```

This will give you a "grub>" prompt. Type

```
find /boot/grub/menu.lst
```

The output will be of the form (hdx,y) (for example (hd1,0) or (hd2,2))

type 

> root (hdx,y)       

setup (hdx)

quit

here you need to replace x and y by the actual  values returned by "find" .So for example if  the output of " find /boot/grub/stage1" was (hd1,0), then do  "root (hd1,0)  setup (hd1) quit"

Reboot, but set you bios to boot from the hard drive on which ubuntu is installed.

Press "Esc" during boot. This should bring up the "grub menu". Select the ubuntu item, but do not press "Enter".  Instead press "e".  Press "e"  again. You should see something like
 
root (hdz,y) 

where  y should have the same values as above. Change it to 

root (hd0,y) 

Press "Enter" and then "b" 

This should boot you into Ubuntu.  Assuming that this worked you will have to edit the "file /boot/grub/menu.lst" 

```
gksudo gedit /boot/grub/menu.lst 
```

will open the file in a new window. Change all  occurrences (there should be at least three) of

root (hdz,y) 

to

root (hd0,y)

also change 

#groot (hdz,y)

to

#groot (hd0,y)

If you have a windows item  in menu.lst you will also have to edit that (asked for help if you need to) 

If you need more detailed instructions or if something goes wrong along the way, come back here and report any error messages you got. Also post the output of

```
sudo fdisk -l
```

Edit: Reading  your post one more time, it seems to me  that you basically already tried what I suggested. But hopefully my post contains some new idea for you.

---

### Post by MorbidAngel on 2007-11-18
did what you said, same message from grub, i hit esc and e and enter, and every other button/combination i could think of, grub message doesn't budge

---

### Post by meierfra on 2007-11-18
So the grub menu did not appear at boot up?

Could you post the output of "sudo fdisk -l"

Couple of  things to try 


1)  Disconnect all the hard drives, except the one containing ubuntu.

2)  Try Super Grub:  [ Hermanzone info on Super Grub]("http://users.bigpond.net.au/hermanzone/SuperGrubDiskPage.html")

---

### Post by MorbidAngel on 2007-11-18
Disk /dev/sda: 74.3 GB, 74355769344 bytes
255 heads, 63 sectors/track, 9039 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        9024    72485248+   7  HPFS/NTFS

Disk /dev/hdc: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hdc1               1        9729    78148161    7  HPFS/NTFS

Disk /dev/sdb: 160.0 GB, 160041885696 bytes
16 heads, 63 sectors/track, 310101 cylinders
Units = cylinders of 1008 * 512 = 516096 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1      310080   156280288+   7  HPFS/NTFS

Disk /dev/hdd: 20.0 GB, 20020396032 bytes
255 heads, 63 sectors/track, 2434 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hdd1   *           1        2327    18691596   83  Linux
/dev/hdd2            2328        2434      859477+   5  Extended
/dev/hdd5            2328        2434      859446   82  Linux swap / Solaris

---

### Post by MorbidAngel on 2007-11-18
tried using SGD, it went well but when trying to fix the linux boot it said "sgd has NOT worked!"  then it said error 15:file not found, which is probably the root of the problem

edit: i also tried unplugging the other hdd's and that did nothing

---

### Post by meierfra on 2007-11-18
>  i also tried unplugging the other hdd's and that did nothing 

What do you mean with "it did nothing"?  Do you get to the grub menu? Any kind of error message?

---

### Post by meierfra on 2007-11-18
With just the one hard drive: boot from the live CD and 
do

```
sudo grub
root (hd0,0)
setup (hd0)
quit
```

But before "quit" copy the contents of the terminal and post it here (Just to make trouble shooting easier)

Reboot and press Esc during boot up (before you get your stage1.5 error message)  to try to  get to the grub menu.

Your IDE drives seem to be /hdc and /hdd  (No /hda and /hdb).  I don't know about much  this,  but it might mean that your drives are plugged in wrongly.

---

### Post by MorbidAngel on 2007-11-18
```
grub> root (hd0,0)

grub> setup (hd0)
 Checking if "/boot/grub/stage1" exists... yes
 Checking if "/boot/grub/stage2" exists... yes
 Checking if "/boot/grub/e2fs_stage1_5" exists... yes
 Running "embed /boot/grub/e2fs_stage1_5 (hd0)"...  17 sectors are embedded.
succeeded
 Running "install /boot/grub/stage1 (hd0) (hd0)1+17 p (hd0,0)/boot/grub/stage2
/boot/grub/menu.lst"... succeeded
Done.

grub> 
```

---

### Post by MorbidAngel on 2007-11-19
> **meierfra said:**
> Your IDE drives seem to be /hdc and /hdd  (No /hda and /hdb).  I don't know about much  this,  but it might mean that your drives are plugged in wrongly.

My first drive was the 2nd sata, it was then switched to a backup when i installed the 1st sata, my main windows partition, the IDE master was in an external enclosure for a year until the enclosure stopped working one day so i installed that and the linux IDE into my computer, they all work fine, but the order's weird

also when i said that unplugging the other drives did nothing i meant that it did not solve the grub boot problem, no new error message or anything

note: the hard drives' names are sda, sdb, hdc, hdd

---

