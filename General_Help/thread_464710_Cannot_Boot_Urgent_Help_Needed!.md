---
title: "Cannot Boot: Urgent Help Needed!"
date: 2007-06-05
forum: General Help
---

### Post by Miniberger on 2007-06-05
A couple of hours ago, I was trying to get my troublesome swap partition to work (sometimes it doesn't seem to mount properly). I don't remember specifically every command I typed in although I tried mkswap /dev/sda5, sudo mount -a, sudo swapon -a and was getting some errors. So, in any case, I opened up /etc/fstab to take a look. I had been running a lot of programs with only 512 MB of physical RAM and no swap, so things were freezing so I closed the fstab with no changes (I never got a chance to look at it). 

Then, strangely, every time I tried to access anything on my hard disk,  I would get error messages saying things like "this item cannot be found" or "cannot open this directory" etc. Every button I pressed gave an error, except shutdown (although the graphical icons in the shutdown menu were missing). After shutting down, my computer loaded BIOS then came up with "Grub 1.5. Error 17" I've read a bit about this, but I don't fully understand why this happens. I have a dual boot with Windows XP and obviously can't access either OS from the HDD (I'm running Feisty Live CD right now). This is a shared computer and it is essential that I be able to boot Windows ASAP. 

Here is my fstab:
```
unionfs / unionfs rw 0 0
tmpfs /tmp tmpfs nosuid,nodev 0 0
/dev/sda2 swap swap defaults 0 0
/dev/sda5 swap swap defaults 0 0
```

This seems abnormal to me. The last record I have of it previously is what I posted on this forum just after my Feisty upgrade (it has been modified slightly since in the swap partition).

```
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/hda2 -- converted during upgrade to edgy
UUID=bb6947b7-2936-4e51-acfd-89d2f70d6fbd / ext3 defaults,errors=remount-ro 0 1
# /dev/hda5 -- converted during upgrade to edgy
/dev/hda5   none   swap   sw   0   0
/dev/cdrom        /media/cdrom0   udf,iso9660 user,noauto     0       0
# /dev/hda6 -- converted during upgrade to edgy
UUID=44EF-6E2D /mnt/shared vfat defaults,uid=1000,gid=100 0 0[html]
```

Any help would be very much appreciated!

Miniberger

Dell Dimension 8300. Pentium 4 2.53gHz "Northwood." 512 MB RAM (2x256) @ 400 mHz. 80 GB HDD. Nvidia MX440 (64MB) graphics. DVD-ROM drive. CD-RW drive. 

40 GB shared fat32. 12.5 GB Ubuntu ext3. 20 GB Windows NTFS. 1 GB Linux Swap.

---

### Post by merlinus on 2007-06-05
I believe you are looking at the live cd fstab.

You need to mount your ubuntu partition, and then look at /etc/fstab under filesystem.

-merlin

---

### Post by Miniberger on 2007-06-05
Yes, you are correct. But I can't seem to mount the filesystem. 

I hate to say this, but it seems I have turned my filesystem into swap. I think I used the wrong drive number in the mkswap command, causing my Ubuntu partition to become swap. 

System monitor lists 13.2 GB of swap, which is about the total of my Ubuntu Filesystem partition and my regular 1 GB linux swap partition.

Can I recover from this error or do I need to reinstall.

Also, is there a way to get into Windows? This is a top priority and could buy me some time if I could do this.

---

### Post by H.E. Pennypacker on 2007-06-05
Can you please install GParted (which should be available via Synaptic), and post a screenshot of the partition table?  We need to know what's going on at this time with your partitions.

Your problem may be solved by restoring Windows MBR, which can be done using fixmbr.  Follow this:

[http://amazingrando.wordpress.com/2007/04/05/fixmbr-is-your-friend/](http://amazingrando.wordpress.com/2007/04/05/fixmbr-is-your-friend/)

---

### Post by Miniberger on 2007-06-05
Yes, looking at Gparted I can see that my former Ubuntu filesystem has become swap. I think I'm simply going to remove the partition (or could I leave it there?) and restore Windows MBR for now, then reinstall Ubuntu later.

---

### Post by Miniberger on 2007-06-05
Oh, and by the way, does anyone know where firefox cookies and bookmarks are stored by default in Windows? I want to back these up before proceeding.

---

### Post by H.E. Pennypacker on 2007-06-05
> Yes, looking at Gparted I can see that my former Ubuntu filesystem has become swap. I think I'm simply going to remove the partition (or could I leave it there?) and restore Windows MBR for now, then reinstall Ubuntu later.

Hmm...if you don't mind, get rid of the Ubuntu partition, as well as swap.  Make sure you backup everything before proceeding.  

Ubuntu, ideally, is installed after Windows has been installed.

> Oh, and by the way, does anyone know where firefox cookies and bookmarks are stored by default in Windows? I want to back these up before proceeding.


Somewhere under user profiles, but then again, I have not used Windows in a long time.  I do know this is a frequently asked question, and Google has the answer.

---

### Post by Miniberger on 2007-06-05
Alright, so I'm trying to get into Windows' recovery console by booting from the CD, but every time I boot my keyboard stops responding. It works as the Windows CD examines my setup but fails as soon as Windows loads and I get the menu. 

The keyboard is OEM, a Dell Quietkey PS/2 model. I've never had this problem before but it does it repeatedly.

Please help me, I need to get this system working!

---

### Post by Miniberger on 2007-06-05
I'm proud to report that I've solved the problem.

As a workaround to the nonresponsive keyboard I tried an almost identical (very slightly updated) Dell Quietkey unit that worked fine. The old unit that didn't work in the recovery module continues to function normally in normal use.


After booting from the Windows CD and launching recovery module, I typed the command "fixmbr" to get rid of grub and it worked like a charm. I restarted and Windows booted normally. There is no lost data on any of the partitions (except of course Ubuntu's ext3 that I accidentally made swap).  

So, all of my partitions remain so all that is left to do is re-install Ubuntu from the live CD to its partition.

A word of advice to all: be careful with the "sudo mkswap" command. If you give the wrong drive/partition number, it will overwrite that partition!

Thanks to all for all of the help.

---

### Post by H.E. Pennypacker on 2007-06-06
Good job, and thanks for reporting back!

Make sure you peruse the General Help forum, and the newbie forum to see if you can help others out as well.   As a brilliant person once said (me), give back to the community what you got out of it.

---

