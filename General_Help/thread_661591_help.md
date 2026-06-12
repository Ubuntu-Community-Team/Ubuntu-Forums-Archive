---
title: "help"
date: 2008-01-08
forum: General Help
---

### Post by munky_nutz on 2008-01-08
I have installed Ubuntu on my computer so that i could choose wether to boot ubuntu or XP when I start up my computer, but I think i did it wron, when i turn on my computer it automatically boots ubuntu, i think i was supposed to create a partition on my hard drive or something

---

### Post by zvacet on 2008-01-08
> Don't display the menu. If the command is used, no menu will be displayed on the control terminal, and the default entry will be booted after the timeout expired. The user can still request the menu to be displayed by pressing <ESC> before the timeout expires.

I hope this will be helpfull to you.

---

### Post by Sef on 2008-01-08
> I have installed Ubuntu on my computer so that i could choose wether to boot ubuntu or XP when I start up my computer, but I think i did it wron, when i turn on my computer it automatically boots ubuntu, i think i was supposed to create a partition on my hard drive or something

Yes, to dual boot you need to create a partition.   If you want to double check if you have a dual boot or not, follow these simple instructions:

Applications > Accessories > Terminal

then type this command:

```
sudo fdisk -l
``` (Small L)

Then paste the results here.

---

### Post by munky_nutz on 2008-01-08
i already tried that and it came up with a list:
Ububtu
Ubuntu (recovery mode)
Ubuntu memtest

Well not those exact names but something similar

---

### Post by zvacet on 2008-01-08
What is going on when you choose first option and hit Enter?

---

### Post by jespdj on 2008-01-08
Doesn't it show Windows XP in the boot menu?

What did you do when you installed Ubuntu; did you use the partition manager to make a partition for Ubuntu, or did you choose "use the whole disk"? If it's the second, then Windows is most likely wiped off your harddisk. :shock:

Do what Sef says: type **sudo fdisk -l** and copy and paste the output here; that way we can tell you if Windows XP is still on your harddisk, or if you deleted it.

---

### Post by munky_nutz on 2008-01-10
[SIZE="1"]what it said is:


Disk /dev/sda: 250.0 GB,  250059350016 bytes
255 heads, 63 sectors/track/ 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x67df67df

       Device Boot     Start            End            Blocks      Id    System
/dev/sda1    *               1        30024    241167748+  83    Linux
/dev/sda2              30025       30401        3028252+    5    Extended
/dev/sda5              30025       30401         3028221    82  Linux swap/Solaris

Disk /dev/sdf:  131 MB,  131072000 bytes
16 heads, 32 sectors/track, 500 cylinders
Units = cylinders of 512 * 512 = 262144 bytes
Disk identifier: 0xd1e5bf71

       Device Boot     Start            End            Blocks      Id    System
/dev/sdf1       *             1           499          127728        6   FAT16

[/SIZE]

---

### Post by munky_nutz on 2008-01-11
does anybody know what has happened????:confused:

---

### Post by jespdj on 2008-01-11
The output shows that you have two harddisks, one called **sda** and one called **sdf**.

sda is 250 GB and contains two Linux partitions. sdf is only 131 MB, that's probably a USB memory stick that you have plugged in into your computer.

It looks like you wiped out your Windows partition. Note that the Ubuntu installer by default uses the whole disk. It also warns you that it is going to format your harddisk. Did you just blindly click next, next, next without reading the warnings? I hope you made a backup of any important data on your Windows partition, because it's gone now. :(

---

### Post by munky_nutz on 2008-01-14
but when i look in computer in locations in ubuntu, it says something about the total space is about 220GB, and i only used around 30GB with windows stuff

---

### Post by erginemr on 2008-01-14
Hi,

Could you please grab your Ubuntu Live CD, boot from there and use GParted (Gnome Partition Editor, under Main Menu -> System ->Administration) to check whether you still have an NTSF (Windows) partition?

---

### Post by ugm6hr on 2008-01-14
> **munky_nutz said:**
> but when i look in computer in locations in ubuntu, it says something about the total space is about 220GB, and i only used around 30GB with windows stuff

But your fdisk -l output lists sda as a 250GB disk, with the whole disk assigned to 2 partitions (Linux and Linux swap).  There is no spare space (see the total cylinders = 30401, with sda1 start=cylinder 1, and sda5 end=30401).

It is fair to say you have wiped your Windows installation.

---

### Post by munky_nutz on 2008-01-15
> **ugm6hr said:**
> It is fair to say you have wiped your Windows installation.


Oh my god, i cannot belive i did that.:(

Should I get a new copy of windows (as i have no disk) or something like that?????

---

### Post by zvacet on 2008-01-15
> Should I get a new copy of windows (as i have no disk) or something like that?????
__________________

Yes,if you want to have windows you have to install them again.I don´t  belive it is hard to find windows Cd.

---

### Post by munky_nutz on 2008-01-25
I have finally got a windows CD, but when i try to install it can't find my hard-drive, it brings up a list of drives for me to use and on all of them says there is no disk in the drive except for my flash drive, what do i do??? i really need windows as ubuntu has messued up my computer

---

### Post by ugm6hr on 2008-01-25
> **munky_nutz said:**
> I have finally got a windows CD, but when i try to install it can't find my hard-drive, it brings up a list of drives for me to use and on all of them says there is no disk in the drive except for my flash drive, what do i do??? i really need windows as ubuntu has messued up my computer

Installing *any* OS in dual-boot is not something for people who are unfamiliar with computers, since things can (and do) go wrong, as you have demonstrated.  This is particularly important if you have not had the foresight to back up important files.

Just to clarify, in case someone else reads this thread, Ubuntu did not mess up your computer - it did exactly what you told it to do, which was to wipe your hard drive and install Ubuntu.

Getting back to your current problem...  Assuming you want Windows alone (i.e. want to wipe Ubuntu forever):
1. Erase Ubuntu partition
This can be achieved by a few different methods
a. Use any of the "Hard Disk Wiping Tools" here: [http://www.ultimatebootcd.com/index.html](http://www.ultimatebootcd.com/index.html) (or just download and use the actual ultimatebootcd)
b. Boot from the Ubuntu LiveCD, go to System-> Administration-> Partition Editor, then just delete all the partitions, create a new partition to fill the whole disc, and format it as NTFS or FAT.
2. Install Windows
Boot from Windows install CD - it should now find the HD.  Remember to reformat the HD from within the Windows Installer when it offers that option.

If, despite your bad experience with Ubuntu installation, you want to dual-boot - just re-post here, and I (or someone else) will guide you through it.  Given you have already lost Windows, there is probably not much more damage you could do anyway.

---

### Post by munky_nutz on 2008-01-30
tried that, and still the only thing it will recognise is my flash drive

---

### Post by munky_nutz on 2008-01-30
> **ugm6hr said:**
> Installing *any* 
If, despite your bad experience with Ubuntu installation, you want to dual-boot - just re-post here, and I (or someone else) will guide you through it.  Given you have already lost Windows, there is probably not much more damage you could do anyway.


I would like to dual-boot, but im not sure how to

---

### Post by ugm6hr on 2008-01-30
> **munky_nutz said:**
> tried that, and still the only thing it will recognise is my flash drive

Tried what?

If you have successfully removed the Ubuntu / Linux partitions, then the only other possibility is that XP can't recognise your HD without specific drivers.  Find that hard to believe though.

Boot the Ubuntu LiveCD and in Terminal - enter the following:
fdisk -l

Dual-booting is explained here:
[http://www.psychocats.net/ubuntu/installing](http://www.psychocats.net/ubuntu/installing)

---

### Post by seventhc on 2008-01-30
Windows can't recognize it b/c it is ext3(most likely scenario)
Boot from the live cd open the terminal type
```
sudo gparted
```delete everything
create a partition for the size you want windows to use
format it as ntfs
create the rest as 1 large partition but don't format it.
Boot to your xp cd, install it on the partition you created for it
when that finishes boot back to the ubuntu live cd
install [COLOR=Red]**Important part **[COLOR=Black]read each screen that comes up, when you get to the screen where you see the slider bar...this is the page you need to read.
Choose "**use remaining free space**" or "use continuous free space"...one of those can't remember exact wording, but you get the idea it will say one or the other. ( there is a radio button for this option)
grab yourself some cheetos or something (not a necessary step) ;)
when it finishes it will ask to reboot or continue using live cd
reboot, and you should have a choice between ubuntu and xp. :)

P.S If xp ends up installing on the entire drive, then before installing ubuntu open gparted again and you can shrink the windows partition.

[/COLOR][/COLOR]

---

### Post by munky_nutz on 2008-01-31
> **seventhc said:**
> Windows can't recognize it b/c it is ext3(most likely scenario)
Boot from the live cd open the terminal type
```
sudo gparted
```delete everything
create a partition for the size you want windows to use
format it as ntfs

P.S If xp ends up installing on the entire drive, then before installing ubuntu open gparted again and you can shrink the windows partition.




Tried that, i had the hard drive formatted as NTFS, wouldn't recognise it, tried FAT32, still wouldn't recognise it. So i have no idea as to what i have to do

---

### Post by zvacet on 2008-01-31
Download [Gparted](http://gparted.sourceforge.net/) and with it you will be able to resize existing partitions or to delete them.if you decide to delete them,and still want to dual boot install Windows first.When you are finish with that follow [this](http://www.psychocats.net/ubuntu/installing) instructions.It will be good to read them all before you start.

---

### Post by munky_nutz on 2008-02-05
I have tried all formats. I have made many partitions of my hard drive, of each one i can use in GParted, but still when I try and install windows all it will recognise is my flash disk and nothing else.

---

### Post by erginemr on 2008-02-05
Also make sure that when you right-click your newly created hard drive in GParted using the version in the GParted Live CD, it has the "boot" flag enabled.

---

### Post by munky_nutz on 2008-02-05
I'll try that then, but still not sure if it'll work

---

