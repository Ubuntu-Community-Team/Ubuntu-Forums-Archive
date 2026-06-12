---
title: "which swap is used by which OS"
date: 2021-04-15
forum: General Help
---

### Post by sofasurfer on 2021-04-15
I have to OS on my drive. On installation each OS received its own swap. How do I know which swap is used by which OS?

---

### Post by CelticWarrior on 2021-04-15
Swap file or swap partition?

---

### Post by sofasurfer on 2021-04-15
Swap partitions. I didn't even know about swap files until about an hour ago and I still do not understand them. My question for now is, can I delete one of the swap partitions. I think the OS just looks for one and uses it. In other words having two swaps is just redundancy. In fact, I think that swap is not even required to operate the system. Is this true?

---

### Post by CelticWarrior on 2021-04-15
Yes, swap isn't required and the more RAM you have the less need for swap. That said, it's good to have some. Since some releases ago Ubuntu uses a swapfile instead of a swap partition by default, more or less how Windows does with its pagefile. The swapfile is a dynamic file in the root file system.

So, first thing to understand is that unless you manually partitioned in advance and then selected "something else" during Ubuntu installation and chose all the required partitions including swap, the installer won't create any additional partition for swap like it did before. Assuming that you did do this sort of manual installation then you should know which is which. Anyway you should look at fstab to make sure which swap partition or swapfile the OS is actually using.

---

### Post by oldfred on 2021-04-15
You can see swap partition with this:
sudo parted -l
or this which also shows UUID if a partition.
lsblk -f

Swap mounted by fstab:
cat /etc/fstab
If swap partition it will be something like this, using your UUID & partition:
# swap was on /dev/sda4 during installation
UUID=3af6a910-59f8-4719-b58c-2e7484d435f0 none            swap    sw              0       0

If swap file:
     /swapfile                                 none            swap    sw              0       0

More info on swap:
man swapon
```
[FONT=monospace][COLOR=#54ff54]**fred@z170-focal-k**[/COLOR][COLOR=#000000]:[/COLOR][COLOR=#5454ff]**~**[/COLOR][COLOR=#000000]$  sudo swapon --show [/COLOR]
[sudo] password for fred:  
NAME      TYPE SIZE USED PRIO 
/swapfile file 1.4G   0B   -2

[/FONT]
```

---

### Post by grahammechanical on 2021-04-15
Following on from what CelticWarrior said - During that manual install process we tell the installer which partition to use as swap and from then on the OS will look for that partition using its UUID number. Delete the partition and it will slow down the loading of the OS as it tries repeatedly to find its swap partition before finally giving up.

It is possible to direct different installs of Linux to use the same partition as swap. I would advise against formatting that partition. I recently made the mistake of allowing a Debian install to share a swap partition with two Ubuntu installs and I allowed it to format the partition and some how the partitions UUID number got changed and now those two Ubuntu installs take a long time to load.

And yes, I did correct the UUIDs in fstab. It did not solve the problem. But then again this is not my thread. :)

We can only run one OS at a time, so it does not break any rules for more than one OS to look to the same partition to use it as swap.

Regards

---

### Post by guiverc on 2021-04-15
> **sofasurfer said:**
> In other words having two swaps is just redundancy. In fact, I think that swap is not even required to operate the system. Is this true?

My system is dual boot (18.04 & the current development system which is *hirsute* currently) and I use both; swap partition & swap files, and don't see the two as redundancy.

Swap partition saves me disk space, as both my OSes can use the one swap partition (*as long as I don't hibernate which I don't*) as if using only swap files, that would mean two swap files on disk of *largish* size.

The swap partition isn't easily changed, so when I need more or less swap I just adjust the swap file for the system that needs the altered space (which adds extra to my shared swap partition).  I like the flexibility of being able to use both.

**Is swap needed to operate?**  

No, but there can be consequences without it (*it'll depend on your resources, plus what you do*)

I stole some RAM from a system (for *testing* purposes in a different box) and didn't expect any side-effects, but the system wasn't using swap & the system slowed to a crawl after I stole the ram.  I quickly added swap, and performance increased back to what it was... In my opinion that box for sure needed *swap* (*at least until I returned it's normal amount of RAM*) though technically it was still working (*just slowly*) without the swap.

The default will depend on what system you're using, what release etc..  There are some releases that default to installing without swap (*the box I stole RAM from was a setup of a Lubuntu release that installed without swap* by default) but others default with swap (most do).

---

### Post by sofasurfer on 2021-04-15
```
$ sudo swapon --show 
NAME      TYPE SIZE  USED PRIO
/swapfile file 1.4G 53.3M   -2


$ sudo parted -l
Model: ATA WD easystore 240 (scsi)
Disk /dev/sda: 240GB
Sector size (logical/physical): 512B/512B
Partition Table: msdos
Disk Flags: 

Number  Start   End     Size    Type      File system  Flags
 2      1048kB  165GB   165GB   extended               boot
 5      1049kB  47.0GB  47.0GB  logical   ext4
 7      47.0GB  47.5GB  537MB   logical   fat32
 8      47.5GB  79.6GB  32.0GB  logical   ext4
 6      79.6GB  149GB   69.0GB  logical   ext4
 3      240GB   240GB   537MB   primary   fat32


$ ls -al /dev/disk/by-uuid/
total 0
drwxr-xr-x 2 root root 140 Apr 15 19:26 .
drwxr-xr-x 7 root root 140 Apr 15 19:26 ..
lrwxrwxrwx 1 root root  10 Apr 15 19:27 899C-4EDA -> ../../sda7
lrwxrwxrwx 1 root root  10 Apr 15 19:27 a7db5469-f563-43c9-834e-8f6d116c13fb -> ../../sda6
lrwxrwxrwx 1 root root  10 Apr 15 19:27 AB92-2888 -> ../../sda3
lrwxrwxrwx 1 root root  10 Apr 15 19:27 b8115106-222d-4a3d-9a13-b0075492c0aa -> ../../sda8
lrwxrwxrwx 1 root root  10 Apr 15 19:27 ba2d1bc6-43be-4376-b31b-c7d2b898d614 -> ../../sda5

```

Operating systems are on sda(5) and sda(8). sda(5) is disfubctional and sda(8) is what I am using. I want to delete the swap that is used by sda(5) but I do not see how to match the swaps up with the coorosponding OS.

---

### Post by CelticWarrior on 2021-04-15
You're using a swapfile. None of your partitions is swap.

---

### Post by sofasurfer on 2021-04-17
Holy cow! Life just keeps getting more confusing. Then what are the two 537 mb partitions that were created when I did the installs? Partitions 7 and 3.

---

### Post by oldfred on 2021-04-17
UEFI requires an ESP which is FAT32.
But you are using MBR(msdos). UEFI wants gpt, but if a drive already is MBR, Ubuntu will not make you change it to gpt to prevent data loss.
Windows in UEFI boot mode requires gpt, and that will auto convert a drive from MBR.

If redoing a drive, better to use gpt. With Ubuntu you can also use gpt with BIOS installs, if you have a bios_grub partition. I converted my first drive to gpt back in 2010 with Windows XP on another MBR drive.

GPT Advantages (older 2010 but still valid)  see post#2 by srs5694:
[http://ubuntuforums.org/showthread.php?t=1457901](http://ubuntuforums.org/showthread.php?t=1457901) & 
[https://wiki.archlinux.org/index.php/GUID_Partition_Table#Advantages_of_GPT](https://wiki.archlinux.org/index.php/GUID_Partition_Table#Advantages_of_GPT)

---

### Post by sofasurfer on 2021-04-18
I'm pretty sure this is out of my ability to comprehend, so I guess as long as my system is operating well I see no reason to be concerned about my little swap issues. 
That being said, oldfred, I'll play along for a bit. I think you are suggesting that I have a UEFI system. I disagree because I do not have a /sys/firmware/efi file. If this is true, can/should I add UEFI in place of mt Bios? Or should I just leave well enough alone?

---

### Post by sofasurfer on 2021-04-18
I think I solved my problem. I have a Dell Inspiron 660. Bios shows 'secure boot' disabled with no option to enable it. It also shows 'legacy' enabled with no other option. So I guess I'm just a legacy guy.

---

### Post by CelticWarrior on 2021-04-19
You had no problem to solve to start with. It was all in your head.

If you have any "secure boot" mention in your firmware then it's UEFI but in your case "wrongly" (as in not recommended because there's absolutely no reason to) installed in Legacy/"BIOS" mode.

> [COLOR=#000000]UEFI requires an ESP which is FAT32.[/COLOR]
[COLOR=#000000]But you are using MBR(msdos). UEFI wants gpt, but if a drive already is MBR, Ubuntu will not make you change it to gpt to prevent data loss.[/COLOR]
[COLOR=#000000]Windows in UEFI boot mode requires gpt, and that will auto convert a drive from MBR.[/COLOR]

[COLOR=#000000]**If redoing a drive, better to use gpt.** With Ubuntu you can also use gpt with BIOS installs, if you have a bios_grub partition. I converted my first drive to gpt back in 2010 with Windows XP on another MBR drive.[/COLOR]

And better to install in UEFI mode in any UEFI based hardware, i.e., anything from at least 2012 or newer.

---

