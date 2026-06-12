---
title: "Partitions are all out of whack..."
date: 2008-02-02
forum: General Help
---

### Post by legoman786 on 2008-02-02
Hey guys, when I installed Ubuntu... little did I know that it would resize my hard drives. I am now stuck with only 70+GB usable of my 500GB HD and I have 20+GB unallocated space on my C. I tried using GParted to resize them, but I'm afraid I'll lose my data on my 500GB.

BTW, can you guys go easy with all the terms and whatnot? I'm new... Thanks.

---

### Post by musther on 2008-02-02
Windows is quite unhelpful, it doesn't tell us what those partitions all are, so do you still have Ubuntu installed or did you remove it?

If you've still got Ubuntu, start it up, open a terminal and type:
```
sudo fdisk -l
```

Then send us the output.

Also, do you want to keep Ubuntu, do you want to keep Windows, where would you like to go from here?

You 'should' be able to use GParted to resize the partitions, but it is possible that something bad could happen, so you should back up first.

When I know what your partitions are, I can offer more of an action plan.

---

### Post by legoman786 on 2008-02-02
I am planning to keep Ubuntu... as I am keeping WinXP. It's more of a learning tool for now. I'm boot into Ubuntu and post the out.

EDIT: Here it is:

Disk /dev/sda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xc2f87748

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        3305    26547381    7  HPFS/NTFS
/dev/sda2            3306        5916    20972857+  83  Linux
/dev/sda3            9462        9729     2152710    f  W95 Ext'd (LBA)
/dev/sda5            9462        9729     2152678+  82  Linux swap / Solaris

Disk /dev/sdb: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xf680977f

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1        9682    77770633+   7  HPFS/NTFS

---

### Post by musther on 2008-02-02
I'm trying to formulate a way for you to fix this without risking losing data, and maximising the use of your disks.

To make sure I give you the best advice I can, I have some more questions.

Are you prepared to re-install Ubuntu.  I assume you haven't had it for long and so don't have to worry about losing lots of data etc?

How much data do you have stored on your windows D:?  Right click on it in 'My Computer' and select properties, have a look at the pie chart and the numbers above it.  (sorry if this is obvious, but I don't know how advanced a user you are).

---

### Post by legoman786 on 2008-02-02
Yeah, I don't mind re-installing Ubuntu. I'm really itchy about my D drive because all of my songs and games are on it. I tried installing Ubuntu on my D drive, but GRUB freaked out and said the partition was not working.

---

### Post by musther on 2008-02-02
Ok, you've got two hard drives.  Each drive has multiple partitions, which are defined ranges in which your computer stores data.  Partitions are functionally separate, for example you can format one and not another.  When windows talks about 'drive C' or 'drive D', it's not talking about drives, it's talking about partitions.

If you're prepared to install ubuntu, the only partitions we're currently concerned about are the ones holding windows, and your data - that's the first partition on each drive.

What I'm going to tentatively suggest is deleting all partitions apart from these to start with, then you'll have:

First Drive:
    Partition 1, Windows C: - about 25GB
    Unallocated space - about 50GB

Second Drive:
    Partition 1, Windows D: - about 75GB
    Unallocated space - about 400GB

In Linux, partitions are referred to something like this 'sda1'.  Don't worry about the sd for now, but the a tells you it's the first drive, and the one tells you it's the first partition.  If you don't mind I'll use this notation, it's the easiest way for you to know what I'm talking about.  

What I would then suggest is creating another partition on the first drive, that will be a2, copying all the data from b1 to a2 and then removing b1.  Then you'll have this:

First Drive:
    Partition 1, Windows C: - about 25GB
    Partition 2 - about 50GB

Second Drive:
    Unallocated space - about 500GB

Then you can decide how you want to lay things out.  Do you want to have Ubuntu on the first or second disk, how much space would you like it to have, where would you like your data partition (your windows D), would you like to share the data partition between Ubuntu and Windows?

For example you could create a vast, 500GB data partition on b, and put all your data there, then remove a2 and install Ubuntu in that space. 

One quick note, when partitioning for Ubuntu, I recommend having three partitions rather than the two that Ubuntu normally creates.  Have a swap (which you just generally need, it's for virtual memory), then you need a / (the root partition, the operating system and installed software goes here, 10GB should be plenty, 20GB to be on the safe side), and then /home.  This differs from what Ubuntu does by default in that it doesn't normally create you a /home.  The advantage of having a /home is that all your files, your data, even configuration files telling the system how you like things to look, your firefox bookmarks etc are stored there.  The advantage of this is that you can reinstall ubuntu, maybe one day remove windows and move things around, and never worry about your data and settings.  You don't have to do this, it's up to you.

---

### Post by legoman786 on 2008-02-02
I have another HDD that I can throw into my computer... It's about 40GB. I'll just throw Ubuntu on that. Then, I'll leave the rest for Windows and my data. Why didn't I do that in the first place? I just don't know if I have another SATA cable around.

Also, to answer your question about how knowledgeable I am... Enough to be A+ certified and more, but only on the Windows side. I've been building computers with my dad for like 7+ years.

I'll go find another SATA cable, if not, then I'll have to follow your suggestions.

---

### Post by legoman786 on 2008-02-02
I found a cable for my 40GB HDD... Made 2 partitions and am installing Gutsy. I deleted the other partitions, but I completely forgot about GRUB and wouldn't let me boot into XP. I'm hoping that GRUB will be restored after the install.

EDIT: Re-install done... GRUB restored... Here's new fdisk out

Disk /dev/sda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xc2f87748

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        9729    78148161    7  HPFS/NTFS

Disk /dev/sdb: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xf680977f

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1       60801   488384001    7  HPFS/NTFS

Disk /dev/sdc: 40.0 GB, 40020664320 bytes
255 heads, 63 sectors/track, 4865 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x000a5e24

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1   *           1        4660    37431418+  83  Linux
/dev/sdc2            4661        4865     1646662+   5  Extended
/dev/sdc5            4661        4865     1646631   82  Linux swap / Solaris

---

### Post by musther on 2008-02-02
Well that's great, I'll stop explaining the difference between partitions and physical drives then!  :-)

---

### Post by musther on 2008-02-02
If GRUB doesn't find everything, take an XP CD, boot to it, go to the recovery console, and then run:

```
fixmbr
```

and

```
fixboot
```

That'll repair the windows boot loader for you!

---

### Post by legoman786 on 2008-02-02
Thanks a lot for your help musther! I can boot into XP, now that the GRUB was restored. Another quick question regarding GRUB... How do I make XP the first in GRUB?

---

### Post by musther on 2008-02-02
A few simple steps to put XP first in the list:

Boot Ubuntu
Open a terminal
Run:
```
sudo gedit /boot/grub/menu.lst
```
Look down the file until you find the boot entries, the ubunt ones will look something like this:
```
title		Ubuntu 7.10, kernel 2.6.22-14-generic
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.22-14-generic root=UUID=e559e062-eebc-4c82-b99b-1f90d3bdca3f ro quiet splash
initrd		/boot/initrd.img-2.6.22-14-generic
quiet
```
The windows one will look a little different.
Move the windows entry to the top of the list, above the Ubuntu ones.

While editing the file you can change the default boot option, the timeout and lots of other fun things, have a look around, but be sensible.

Remember that in Linux config files, lines starting with #, or any text after a # is a comment, you can do what you want with those lines, or make your own comments for future reference:
#This is a comment,
timeout=3 #This is also a comment, but the bit before the # is not...  fun eh?

Save.
Reboot.

So now you have windows and ubuntu installed, do you still have small partitions on big drives?  I was thinking about it, and expanding NTFS partitions (using gparted) should be really rather safe - although nothing is ever certain.

Anyway, if you want to resize the partitions, use synaptic to install gparted, then do it.

Best of luck with Ubuntu :-)

---

### Post by legoman786 on 2008-02-03
I found it

```
title		Ubuntu 7.10, kernel 2.6.22-14-generic
root		(hd2,0)
kernel		/boot/vmlinuz-2.6.22-14-generic root=UUID=a8354266-e78b-481d-9113-7dee74e643e9 ro quiet splash
initrd		/boot/initrd.img-2.6.22-14-generic
quiet

title		Ubuntu 7.10, kernel 2.6.22-14-generic (recovery mode)
root		(hd2,0)
kernel		/boot/vmlinuz-2.6.22-14-generic root=UUID=a8354266-e78b-481d-9113-7dee74e643e9 ro single
initrd		/boot/initrd.img-2.6.22-14-generic

title		Ubuntu 7.10, memtest86+
root		(hd2,0)
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title		Microsoft Windows XP Professional
root		(hd0,0)
savedefault
makeactive
chainloader	+1
```

Do I just move the XP entry to the top and save?

---

### Post by forestpixie on 2008-02-03
no don't move the xp entry - just amend the default 

near the top of the menu .lst there is a bit that looks like 

>  You can specify 'saved' instead of a number. In this case, the default entry
# is the entry saved with the command 'savedefault'.
# WARNING: If you are using dmraid do not use 'savedefault' or your
# array will desync and will not let you boot your system.
default         0

the zero can be changed- count the occurrences of 'title' that are not preceded by #
and change the number to suit - when you boot the default will have changed, you must count from zero as well - so if you've posted all the relevant parts of your list change it to 4

---

### Post by musther on 2008-02-03
It's best NOT to do it the way forestpixie said, here's why.

If your menu.lst file says (in real world language:

```
Boot the third entry:

0 - Ubuntu
1 - Ubuntu Rescue
2 - Memtest
3 - Windows
```

Then when you get a kernel update, and another entry is automatically added to GRUB, it'll end up saying this:

```
Boot the third entry:

0 - Ubuntu 2.7
1 - Ubuntu 2.6
2 - Ubuntu Rescue
3 - Memtest
4 - Windows
```

Which of course will end up booting memtest all the time.

If you instead put windows to the first option, it'll always work.  This is why the default option should always be the first option in the menu.

So yes, move the XP entry above the Ubuntu ones, and change the default to match.

---

### Post by forestpixie on 2008-02-03
and if you put xp into the debian auto magic part it'll go when there's a kernel update afaik

---

### Post by musther on 2008-02-03
Well, you could put the XP entry above:
```

### BEGIN AUTOMAGIC KERNELS LIST
## lines between the AUTOMAGIC KERNELS LIST markers will be modified
## by the debian update-grub script except for the default options below
```

---

### Post by forestpixie on 2008-02-03
yea that'd be better I guess as long as it's outside the automagic list, but I'm not sure what'd happen when there's a kernel update - never wanted to have win as default once I'd got this going :)

still now the op knows both ways

---

### Post by musther on 2008-02-03
I don't have windows to boot, default or otherwise.  But I have set somebody up this way, and it worked when they got a kernel update, so hopefully that'll still be the case.  Anyway, he'll know how to fix it now if anything did happen.

---

### Post by legoman786 on 2008-02-03
Thanks guys... I'll do a restart and see if anything has changed.

EDIT: Thanks again guys... Now that the boot priority has been sorted, I can start asking the real questions.

---

