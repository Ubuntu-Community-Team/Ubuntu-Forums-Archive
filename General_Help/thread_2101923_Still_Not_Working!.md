---
title: "Still Not Working!"
date: 2013-01-05
forum: General Help
---

### Post by drummermike on 2013-01-05
It all came about when I enrolled in a Computer Science degree at De Monfort University and quickly realised I needed to have a Linux OS installed on my laptop. This would be my first time on Linux. So, I had to dual boot alongside Windows 7, which came with the laptop. Bearing in mind, this is in September and I hadn't the knowledge of what it would be like (how gruelling grub would be.)

So, it comes to December and I've installed a few components such as jEdit, Wireshark, Netkit, Ettercap and others. And the boot starts to increasingly get worse and worse in that I was having to turn on and off the laptop at least a couple of times to achieve a full boot into Ubuntu (Windows never having a problem of booting.) One day it just decides to not boot at all, with the generic blank black screen with the typing prompt. Me, being the inquisitive noob attempts "ls" to which there is no response. With it being Ubuntu 12.04 LTS, I decided to scratch the whole of the two partitions for it ("/" and "swap") and install 12.10 with the same partitions. This time, it takes a mere day for the boot to **** up again and Boot Repair cannot do anything about it:

_[http://paste2.org/p/2702254](http://paste2.org/p/2702254)_

**Could someone please help? I need to get this up and running before the next term starts and we're doing Haskell!**

My laptop's specs:

[I]Operating System: Windows 7 Home Premium 64-bit (6.1, Build 7601) Service Pack 1 (7601.win7sp1_gdr.120830-0333)
Language: English (Regional Setting: English)
System Manufacturer: LENOVO
System Model: IdeaPad Z580    
BIOS: Phoenix BIOS SC-T v2.2
Processor: Intel(R) Core(TM) i5-3210M CPU @ 2.50GHz (4 CPUs), ~2.5GHz
Memory: 8192MB RAM
Available OS Memory: 8056MB RAM
Page File: 2393MB used, 13715MB available
Windows Dir: C:\Windows
DirectX Version: DirectX 11

[/I]Partitions (as stated in the link above: )
/dev/sda1    *          2,048       411,647       409,600   7 NTFS / exFAT / HPFS                           - Windows (boot?) 
/dev/sda2             411,648 1,172,286,647 1,171,875,000   7 NTFS / exFAT / HPFS        - Windows 
/dev/sda3       1,172,287,486 1,424,185,343   251,897,858   5 Extended                                 - Windows (laptop came dual partitioned) 
/dev/sda5       1,172,287,488 1,392,936,959   220,649,472  83 Linux                                        - Ubuntu 
/dev/sda6       1,392,939,008 1,424,185,343    31,246,336  82 Linux swap / Solaris     - Ubuntu 
/dev/sda4       1,424,185,344 1,465,149,167    40,963,824  12 Compaq diagnostics    - Windows (Recovery)
.../sdb being the flash drive I booted the Boot-Repair-Disk from

---

### Post by YannBuntu on 2013-01-05
Hi
one possible issue is that currently your Ubuntu boot files are far from the start of the disc.
Please follow this procedure from step2: [https://help.ubuntu.com/community/InstallingUbuntuOnBigDisk](https://help.ubuntu.com/community/InstallingUbuntuOnBigDisk)

---

### Post by drummermike on 2013-01-06
> **YannBuntu said:**
> Hi
one possible issue is that currently your Ubuntu boot files are far from the start of the disc.
Please follow this procedure from step2: [https://help.ubuntu.com/community/InstallingUbuntuOnBigDisk](https://help.ubuntu.com/community/InstallingUbuntuOnBigDisk)

Unfortunately, this has not helped. As with when I installed Ubuntu for the second and third time (12.04 and 12.10 respectively) the "grub rescue>" prompt was displayed. I had to again do a "Recommended Boot-Repair," which then allowed me a few more startups and alas, it is once again no more.

I should say that the first time I did install Ubuntu (in September) it was with an additional two partitions: "/boot" and "/home." This was because I was new to doing it and found this article recommending it. Only when it came to reinstalling it did I realise that was best suited for servers (I was told.) So, invariably, I don't think the last suggestion of creating a "/boot" partition will work.

What is wrong with this laptop?!

---

### Post by AstroLlama on 2013-01-06
You really chose to start out with one of the most difficult things! I had a similar problem in the past, in my case windows boot loader was only recognizing the ubuntu partition (placed deep into the HD) some of the time and the other times would fail. 

My suggestion is to not use separate /boot or /home partitions yet. You can create those partitions later if you wish. Focus on one problem at a time! :)

where did you install Grub?

---

### Post by YannBuntu on 2013-01-06
> **drummermike said:**
> "/boot" and "/home." (...) was best suited for servers (I was told.)

The person who wrote that is wrong, believe me. See [https://help.ubuntu.com/community/DiskSpace](https://help.ubuntu.com/community/DiskSpace) for more info.

---

### Post by drummermike on 2013-01-07
> **AstroLlama said:**
> You really chose to start out with one of the most difficult things! I had a similar problem in the past, in my case windows boot loader was only recognizing the ubuntu partition (placed deep into the HD) some of the time and the other times would fail. 

My suggestion is to not use separate /boot or /home partitions yet. You can create those partitions later if you wish. Focus on one problem at a time! :)

where did you install Grub?

Of all the options, it was recommended (through Boot-Repair-Disk) that it be installed on "sda" - as in the whole hard drive, not "sda1" or "sda2."

I gather that this is because the grub menu is used to initiate the dual boot process via providing a menu upon starting up the system. (?)

Edit:

> **YannBuntu said:**
> The person who wrote that is wrong, believe me. See [https://help.ubuntu.com/community/DiskSpace](https://help.ubuntu.com/community/DiskSpace) for more info.

So, would you recommend adding in those partitions? (Although they did not seem to help in my case.)

---

### Post by YannBuntu on 2013-01-08
> **drummermike said:**
> So, would you recommend adding in those partitions?

only the /boot partition. See [https://help.ubuntu.com/community/BootPartition](https://help.ubuntu.com/community/BootPartition)

---

### Post by mastablasta on 2013-01-09
i really hate these preinstalled notebooks but the reality is most of them come like that.
 
anyway i think boot partition i needed if you have UEFI.
 
also your bootinfo script says unknown file type for swap partition. i am not sure if this is how it is supposed to be.

---

### Post by drummermike on 2013-01-10
I will add a "/boot" partition and see how it fairs.

As I have explained, there was a "/boot" and "/home" partition on here before and it stopped booting eventually.

---

### Post by drummermike on 2013-01-12
It has reverted back to its condition of not starting, again!

Surely there is some other way.

---

### Post by YannBuntu on 2013-01-12
Please run the Recommended Repair and indicate the new URL, so that we know where you are now.

---

### Post by drummermike on 2013-01-14
First of all, I resized the largest Windows partition by 1GB and then realised it should really be right at the beginning of the Ubuntu partition so shrunk that.

The following URL was what I got when I attempted to install the "/boot" partition as detailed in the link that was given:

[http://paste.ubuntu.com/1531868/](http://paste.ubuntu.com/1531868/)

And this is the URL that was given when "Recommended Repair" was done due to the fact that Ubuntu had disappeared from the grub menu:

[http://paste.ubuntu.com/1531923/](http://paste.ubuntu.com/1531923/)

It still will not start.

---

### Post by d4m1r on 2013-01-14
Ok first off, since that is a newer laptop, does it come with a standard BIOS or with a UEFI based system? That might explain why you are having a hard time booting into Ubuntu...

---

### Post by drummermike on 2013-01-14
> **d4m1r said:**
> Ok first off, since that is a newer laptop, does it come with a standard BIOS or with a UEFI based system? That might explain why you are having a hard time booting into Ubuntu...

Err, is it true that if it has a UEFI-based system, you can move the mouse in the BIOS menu? Because if it is, then my laptop just has standard BIOS.

---

### Post by YannBuntu on 2013-01-14
Hi
Your computer has an UEFI firmware, and is currently set up to boot your live disc in UEFI mode.
AND your boot files are still too far (>100GB) from the start of the disk.

I recommend you create a /boot partition, and make your BIOS boot the HDD in Legacy (not UEFI) mode.

> **drummermike said:**
> Err, is it true that if it has a UEFI-based system, you can move the mouse in the BIOS menu? 

No, this statement is not true. There are some UEFI firmwares where you can't use the mouse. See [https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI)

---

### Post by drummermike on 2013-01-15
> **YannBuntu said:**
> 
AND your boot files are still too far (>100GB) from the start of the disk.

I am unsure how to safely create a "/boot" partition at the start of the disk (or below 100GB from the start.) I have been told not to touch the 200MB Windows recovery partition right at the beginning and I am not sure how to create space at the beginning of the second (largest) Windows partition - at least using the Disk Management feature on Windows. (I have also been told not to configure Windows partitions with GParted.)

This is why the "/boot" partition I attempted to install was in fourth place supposedly because for some reason when I tried to make space at the beginning of the Ubuntu partition it wouldn't let me fill all of the gaps and insisted 1MB should be left unallocated. This is with GParted btw.

---

### Post by drummermike on 2013-01-15
> **YannBuntu said:**
> make your BIOS boot the HDD in Legacy (not UEFI) mode.

Do I really need to this? Should I not just try to create the "/boot" partition at the beginning of the disk first?

---

### Post by drummermike on 2013-01-16
Bump.

---

### Post by brusegadi on 2013-01-16
Try that.  See 

[https://en.wikipedia.org/wiki/UEFI#Criticism](https://en.wikipedia.org/wiki/UEFI#Criticism)

UEFI makes it harder to install another OS.

---

### Post by Giveingitago on 2013-01-16
I struggled for a few days tying to install Ubuntu 12.10 from a live CD on my new HP ENY 6 Sleekbook. Used the 'do something else' option with the install process. Found the Envy would just keep booting into windows. Found the following issues not sure which solution cured the install issue. May help you.

The Sleekbook had 4 primary patitions:

1)Bios/Win7 boot
2) Win7
3)HP TOOLS
4)Win 7 Recovery.

I backup the last 2 partitions into the windows partition and onto a USB Hardisk.

1) Eventually used the HP TOOLS partition as a separate Primary partition for the Ubuntu Boot partition. Thought perhaps the BIOS needed to point at a Primary partition ?
2) Used the HP recovery partition as an Extended partition for Ubuntu. Found a boundary issue, changed the Gparted default partitioning from MegaByte to Sector alignment.
3) Found Ubuntu or Gparted mounted the 2 remaining NTFS partitions during the install, unmounted the 1st win 7 boot partition before proceeding with the install process. I thought Grub needed access to the first few sectors on the hard disk. Final partitioning looked like this:

[http://www.divnut.com/Ubuntu/Screenshot_Gparted_HPENVY6_1006SA.png](http://www.divnut.com/Ubuntu/Screenshot_Gparted_HPENVY6_1006SA.png)

Hope this helps.

---

### Post by brusegadi on 2013-01-16
I was wondering, do you think its possible that the UEFI installation was installed along a legacy installation?  I have never dealt with the UEFI stuff, and it looks like a small mistake can grow out of proportions.  If I were you, I would make a backup. Then, I would make two primary partitions on the hard drive.  On the first, install ubuntu (use logical partitions within this partition.)  Once done, I would install windows in the second partition.

I have read before that GRUB is nicer when dual booting than Windows, so it is worth a try.  Then, make sure that everything is done in either legacy or EFI.    Sorry for this issue, I wish I could be more helpful :(

---

### Post by prodigy_ on 2013-01-17
Have you thought about using virtualization (VMWare, VirtualBox) instead of dual boot? This is more practical in most cases (unless you really need both OS on bare hardware for some reason) and might be the easiest solution.

If you really want to fix **Grub** dual boot (e.g. for learning purposes) I'd suggest making a backup and starting from scratch. Otherwise your might find [this](http://www.iceflatline.com/2009/09/how-to-dual-boot-windows-7-and-linux-using-bcdedit/) useful (you can actually skip most of the HOWTO since you already have both OS installed).

---

### Post by drummermike on 2013-01-17
> **prodigy_ said:**
> Have you thought about using virtualization (VMWare, VirtualBox) instead of dual boot? This is more practical in most cases (unless you really need both OS on bare hardware for some reason) and might be the easiest solution.

I have tried this and I found it didn't really fare well with my computer. It would often be slow and almost fractional particularly when using netkit in a Virtual Box Ubuntu. Plus, I like having the ability to boot into the actual OS; Ubuntu is a decent distribution.

> **prodigy_ said:**
> If you really want to fix **Grub** dual boot (e.g. for learning purposes) I'd suggest making a backup and starting from scratch. Otherwise your might find [this]("http://www.iceflatline.com/2009/09/how-to-dual-boot-windows-7-and-linux-using-bcdedit/") useful (you can actually skip most of the HOWTO since you already have both OS installed).

I am in no way qualified to do this. I definately would not want to **** up the recovery partition for Windows or anything else on the disk for that matter. Plus, I just don't have the time to sit here and wipe the disk and start over. I'm a full time student for Christ's sake!

---

### Post by drummermike on 2013-01-17
How the hell would I go about booting the UEFI in legacy mode anyway?

---

### Post by drummermike on 2013-01-18
I've got a boot info summary here:

[http://www.linuxforums.org/forum/ubuntu-linux/194317-ubuntu-not-working-after-several-failed-fixes-2.html](http://www.linuxforums.org/forum/ubuntu-linux/194317-ubuntu-not-working-after-several-failed-fixes-2.html)

---

### Post by Joao Lacerda on 2013-01-19
Hi Friend!!

I have had similar problem, and in my case it was hardware problem,
I had done a couple of hard shutdown, because the system was not responding, 
and that have caused damage to the hard disk (MBR), I bought a new hd and 
it works fine again, after that I have stop using Microsoft, and changed to 
this wonderful system. (UBUNTU oh!!! boy I love it!!!) 
I hope that for you it will different.
(not a hardware problem)

kind regards.

João

---

### Post by drummermike on 2013-01-20
> **Joao Lacerda said:**
> Hi Friend!!

I have had similar problem, and in my case it was hardware problem,
I had done a couple of hard shutdown, because the system was not responding, 
and that have caused damage to the hard disk (MBR), I bought a new hd and 
it works fine again, after that I have stop using Microsoft, and changed to 
this wonderful system. (UBUNTU oh!!! boy I love it!!!) 
I hope that for you it will different.
(not a hardware problem)

kind regards.

João

I'm pretty positive it's not a hardware problem, but thanks for the help!

---

### Post by prodigy_ on 2013-01-23
> **drummermike said:**
> I have tried this and I found it didn't really fare well with my computer. It would often be slow and almost fractional particularly when using netkit in a Virtual Box Ubuntu.
You need to check if virtualization is enabled in BIOS. It's usually disabled by default. Can really speed things up.

> **drummermike said:**
> I am in no way qualified to do this. I definately would not want to **** up the recovery partition for Windows or anything else on the disk for that matter. Plus, I just don't have the time to sit here and wipe the disk and start over. I'm a full time student for Christ's sake!
Qualified to do what? :) It's a step-by-step HOWTO on how to use Windows 7 bootloader to boot Linux. But of course it's your choice whether to try it or not. Just bear in mind that simple solutions aren't always available.

---

