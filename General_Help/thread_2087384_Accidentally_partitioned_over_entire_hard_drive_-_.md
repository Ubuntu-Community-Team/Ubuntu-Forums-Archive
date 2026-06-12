---
title: "Accidentally partitioned over entire hard drive - cannot boot"
date: 2012-11-23
forum: General Help
---

### Post by DaimyoKirby on 2012-11-23
Background: So yesterday I was following [these instructions]("https://help.ubuntu.com/community/Partitioning/Home/Moving") to move my /home folder to a separate partition, but after partitioning it, whenever I tried to boot to my Zorin 6 installation, I got a black screen and "could not write bytes: Broken pipe", along with other, varying stuff. I continued to follow those instructions from a liveUSB of Xubuntu 12.10, but it was getting too complicated, so I just moved the files I wanted to keep onto the new partition using `gksu thunar`, and booted into my liveUSB to install Xubuntu 12.10 over Zorin.

I started the installer after choosing "Try Xubuntu without installing", and when it came to the option on how to partition, I chose "install over Zorin 6", and checked the "Use LVM" option. Then I clicked forward, but some error came up (I can't really remember, I started to panic shortly after this), and when I closed out of the installer and opened gParted to see what had happened, I saw that I had two partitions - a 255Mb ext4, and a new 76gb "unknown" partition, with a flag of "LVM". When I tried to mount the 32gb partition still listed on my desktop, it was unable to - it got some error of "not enough space".

And this is where I really started getting frantic - I tried to open the installer again, it wouldn't, so I shut down, and rebooted the liveUSB, this time choosing "Install Xubuntu" - I followed the same steps, and resigned myself that I lost the data, but after selecting the option to erase the whole disk and install, it said that the installer had encountered an unrecoverable error, and it was going to boot a live desktop so I can see what went wrong, or try the installer again; it just hung on a black screen.

Question: Is there any way I can recover my data without being able to boot the installed OS?

I have a considerable amount of music, game data, etc. that I would really not want to lose, so any help is appreciated.

---

### Post by Bashing-om on 2012-11-23
It is possible that your data has not been overwritten. To look and see what the system sees:
boot up the installCD -> "try" mode, Go ahead and boot to the desk top;
ctl+alt+t for a terminal:
in terminal enter the following:
```
sudo fdisk -lu
 sudo parted /dev/sda unit s print

```these commands give partition information, if the partitions still exist, Might find a way to pull the files. (else; many have had good results from "testdisk" file recovery CD).
[INDENT][INDENT]just try'n to help <== BDQ

[/INDENT][/INDENT]

---

### Post by sdowney717 on 2012-11-23
You can try 'testdisk'
which is made to recover lost partitions

[http://www.cgsecurity.org/wiki/TestDisk_Livecd](http://www.cgsecurity.org/wiki/TestDisk_Livecd)

Download a live cd version and you might get it back.

---

### Post by DaimyoKirby on 2012-11-23
I ran TestDisk from a LiveUSB of Xubuntu 12.10, and managed to recover my two partitions, exactly how they were.
However, I seem to have made another fatal step.
I started up the installer, and chose "Replace Zorin OS 6 with Xubuntu 12.10", thinking this would only write to the partition that had Zorin installed, not the (nearly) empty partition. After the installation, I noticed I once again only had a single partition (LVM), meaning that my files I had backed up on the non-Zorin partition are gone as well.

I'm running a bunch of different things through TestDisk right now, but is there any way I can recover those files/partition following this repartitioning and reformatting?

---

