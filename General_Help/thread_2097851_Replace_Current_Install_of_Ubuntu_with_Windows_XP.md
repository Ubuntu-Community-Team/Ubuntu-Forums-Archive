---
title: "Replace Current Install of Ubuntu with Windows XP"
date: 2012-12-24
forum: General Help
---

### Post by mrdiabolilc on 2012-12-24
Before you rage, yes I know- why would anyone want to go back to MS windows?

Well, I have a relatively old laptop and without being able to install my dell drivers, my already inefficient system can't run as well as it once did.

On a separate note, I initially installed Ubuntu about 9 months ago to get rid of a particularly nasty virus on windows and figured it would be easy to go back later. It was not.

I mainly use my pc for playing games, etc so linux isn't the best environment for that. I have spent hours running through tutorial after tutorial to compile source code for various games and install different emulators for n64/gameboyadvance/etc. Point being, I have had my fun with this os, but feel it is time to go back to windows.

A graphics update I installed because of a steam linux beta prompt broke my gfx settings or something and wouldn't allow me to boot up because of screen resolution issues, so I have formated my pc back to Ubuntu/Lubuntu, and my hdd is nearly clean.

I have set up a 13gb partition file system set to ntfs and checked the boot flag... total hdd space is 40gb.

Now for my question... (sorry for the long introduction) How can I either a. dual boot windows or 2. I would prefer to completely remove linux os and go back to windows xp?

It should be noted that I need step by step noob friendly instructions and also when I initially installed ubuntu I did a complete format of my hdd. Boot disks and usb drives are never recognized by my system for some reason, and I do have an .iso for Windows xp.

pl0x help somebody!!!

---

### Post by mrdiabolilc on 2012-12-24
bump

---

### Post by N00b-un-2 on 2012-12-24
depending on what you want to do, the solution is fairly simple.  If you want to dual boot Ubuntu with Windows, first you'll need to create an NTFS partition to install Windows XP on.  You can do this using gparted.  I would recommend creating a partition of at least 40GB or larger.  Then after creating the partition, reboot using the XP install CD and install Windows on the new NTFS partition.  You'll lose the ability to boot into Linux at this point, but that's easily fixable.
You can reinstall GRUB by booting into a live CD and chroot into your existing install
```
sudo -s
mount /dev/sda1 /mnt
mount --bind /proc /mnt/proc
mount --bind /dev /mnt/dev
chroot /mnt
```

and then just reinstall GRUB to the hard drive MBR
```
grub-install /dev/sda
```
then reboot.

If all you want to do is simply wipe the hard drive and install Windows, there are several ways to go about doing it.  You can zero out the hard drive using dd from a live CD
```
sudo dd if=/dev/zero of=/dev/sda
```
or if you feel the need to securely wipe your hard drive you can use a tool like DBAN [http://www.dban.org/]("http://www.dban.org/")

If you plan on switching operating systems, it's typically a good practice to wipe a drive before installing.  MBRs can get a little goofy when written to repeatedly and can cause booting errors.

Once you've wiped your drive, just install Windows as normal and proceed from there.

*** Oh, and as a courtesy to the other members of this community, please refrain from bumping threads within 24 hours of your initial post.  Keep in mind that the forums are just that -- forums.  If you need an answer in what you consider a timely fashion perhaps you may consider purchasing technical support from Canonical.

---

### Post by mrdiabolilc on 2012-12-24
Thanks for the suggestions, I have already created multiple windows xp boot disks using both cd and usb format, and when I boot from them at startup, I usually get a blinking cursor that lasts for hours or with the cd CDBOOT: MEMORY OVERFLOW ERROR. It never even let's me get to the point of designating which partition to install windows on. I feel like some necessary files have been wiped from my hdd to install windows when I put ubuntu on it. So, your first option I have tried to no avail. I am hesitant to do the 2nd because once I wipe my hdd, I am afraid it will reject the windows bootdisk still. Any idea what is going on here?

**I will try to be patient about bumping this, it's just I have searched many tutorials on and off for months to try and do this with no success. Thank you for your time I do really appreciate it.

---

### Post by oldfred on 2012-12-24
Do you have boot flag on NTFS partition?

We have many who only have an XP upgrade CD, not the full install CD. An upgrade will only upgrade an XP that is already installed.

---

### Post by mrdiabolilc on 2012-12-24
> **oldfred said:**
> Do you have boot flag on NTFS partition?

We have many who only have an XP upgrade CD, not the full install CD. An upgrade will only upgrade an XP that is already installed.

yes, I went into gparted and on the ntfs partition have checked off boot flag. I just realized that it won't even let me boot off the ubuntu 12.04 live cd I just burned. Gives me the endless blinking cursor when I try to boot from disk. I installed ubuntu on this computer with a flash drive. It is almost as if ubuntu doesn't know how to communicate with my cd drive... Not sure what bearing this may have, but when I originally installed ubuntu I formatted all partitions of my hdd when prompted, removing everything that was windows. Is this why I can't reinstall?

---

### Post by oldfred on 2012-12-25
Also is NTFS partition a primary partition or sda1 thru sda4?

Sometimes systems BIOS settings get messed up with lots of activity and a cold boot resets everything. Totally power down, if laptop remove battery and hold power switch to drain  power. Wait a minute or two and then totally reboot.

Also CD lens may need cleaning?
       How to clean CD lens:
[http://members.iinet.net.au/~herman546/p27.html](http://members.iinet.net.au/~herman546/p27.html)

---

### Post by mrdiabolilc on 2012-12-25
> **oldfred said:**
> Also is NTFS partition a primary partition or sda1 thru sda4?

Sometimes systems BIOS settings get messed up with lots of activity and a cold boot resets everything. Totally power down, if laptop remove battery and hold power switch to drain  power. Wait a minute or two and then totally reboot.

Also CD lens may need cleaning?
       How to clean CD lens:
[http://members.iinet.net.au/~herman546/p27.html]("http://members.iinet.net.au/%7Eherman546/p27.html")

I have recently put yet another clean install of ubuntu on the laptop, so there is no longer an ntsf partition, I believe when it was on there it was sda1 when it was the entire partition or sda2 when i split the hdd in attempt to dual boot. Should it be set as primary to install windows on it?

okay, I will give this a shot, fred... I have formatted the hdd multiple times in the past few years.

I just got done nuking my hdd with dban and from a live cd used gparted to change my entire hdd to one ntfs partition. also used a program which was supposed to fix my mbr. still got same error messages when attempting to boot from a windows disk (CDBOOT:MEMORY OVERFLOW ERROR or checking your hardware settings...).

all I want for christmas is my old os back!! keep the suggestions coming, thanks everyone for taking time out of your holiday to help me out with this:p

---

### Post by oldfred on 2012-12-25
Do you have AHCI turned on? I had to turn that on to get SSD to use trim, but XP does not work and the normal install does not have the AHCI drivers. Try IDE.

May also be a SATA driver issue, if not original drive?

---

### Post by mrdiabolilc on 2012-12-26
waited until battery ran dead unplugged from power source then unplugged battery and plugged back in. booted from windows xp disk, still got memory overflow error. will try checking off those other options... starting to lose hope. thanks for trying to help.

---

### Post by N00b-un-2 on 2012-12-26
are you sure you have a valid Genuine Windows XP CD?  the behavior your laptop is exhibiting sounds like you may be trying to use an OEM copy of Windows that is not keyed to you laptop's motherboard.  I remember a long time ago I tried using a recovery disk that came with one HP computer I owned on an eMachine computer and it would fail with memory errors.  This was back before I knew that an OEM Windows install CD would not work on any computer but the one it was keyed to, or more specifically the EXACT motherboard it is keyed to... but that's another story altogether.

When installing Windows XP, I've often run into issues regarding power management and SATA drivers, most of which were alleviated by the release of SP3.  In the past, I've had to customize my own Windows XP disks by slip-streaming service packs and SATA drivers among other things into them using a program called N-Lite.

You mentioned using "a program" to fix your MBR.  you did not specify what program or how you used it, nor what platform it was on (windows recovery environment or Linux terminal, or other...)

As I'd said before, ESPECIALLY if you have partitioned a disk multiple times over the years, your MBR can become corrupted and unrecoverable without a low level wipe. I highly recommend using DBAN for this, as it cleanly wipes and eradicates all data and partitioning information from disks relatively efficiently.  depending on the size of the disk and what wiping method you use it could take between a few hours to a few days to completely wipe a disk.  For examply, I have "zeroed" out an 80GB SATA drive using DBAN in about 2 hours, and I securely wiped a 2TB disk using DOD secure method and it took 5 days.

But disregarding any concerns for data recovery, using dd to zero out your hard drive will accomplish the same thing.

---

