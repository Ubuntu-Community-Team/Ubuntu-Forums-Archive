---
title: "cannot boot - Grub error 17"
date: 2008-01-27
forum: General Help
---

### Post by marchino61 on 2008-01-27
Hello Everyone

I just installed Ubuntu 7.10 two days ago. It worked OK at first, but after using it about 3 times, I got the above boot error.

I can no longer boot either XP Pro or Ubuntu. I am using a Dell Inspiron 6000 laptop.

The problem may have been caused by editing partitions in XP using Paragon Partition Manager (I wanted to decrease the size of the partition automatically created for Ubuntu during the installation). I have since put the partitions back as they were but to no effect.

I have tried many things suggested in these forums and elsewhere, including Super Grub from USB. This allows me to boot XP (I have not reinstalled the XP boot, instead I boot via the USB drive each time).

However, I cannot fix my Ubuntu boot. The option "boot Linux directly" also does not work for me. I can mount my filesystem from the live CD and edit my menu.lst file.

I have only one disk. All USB and fireware devices have been disconnected. 

I can read and write my Linux partition using Ext2 IFS in Windows (much quicker than the Live CD, which I find very, VERY slow).

Here is the result of fdisk:


Disk /dev/sda: 60.0 GB, 60011642880 bytes
255 heads, 63 sectors/track, 7296 cylinders, total 117210240 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x41ab2316

   
Device Boot      Start         End      Blocks   Id  System

/dev/sda1              63      112454       56196   de  Dell Utility

/dev/sda2   *      112455    24691904    12289725    7  HPFS/NTFS

/dev/sda4        24691905   110896694    43102395    f  W95 Ext'd (LBA)

/dev/sda5        24691968    31246424     3277228+   b  W95 FAT32

/dev/sda6        31246488    52227314    10490413+   7  HPFS/NTFS

/dev/sda7        52227378    70669934     9221278+   7  HPFS/NTFS

/dev/sda8   *    70669998    81802979     5566491   83  Linux

/dev/sda9        81803043    82413449      305203+  82  Linux swap / Solaris

/dev/sda10       82413513   102703544    10145016    7  HPFS/NTFS

/dev/sda11      102703608   110896694     4096543+   7  HPFS/NTFS

And here is my menu.lst:


title		Ubuntu 7.10, kernel 2.6.22-14-generic
root		(hd0,7)
kernel		/boot/vmlinuz-2.6.22-14-generic root=UUID=3df6f425-f1c8-45bf-81b9-71d510b4d578 ro quiet splash
initrd		/boot/initrd.img-2.6.22-14-generic
quiet

title		Ubuntu 7.10, kernel 2.6.22-14-generic (recovery mode)
root		(hd0,7)
kernel		/boot/vmlinuz-2.6.22-14-generic root=UUID=3df6f425-f1c8-45bf-81b9-71d510b4d578 ro single
initrd		/boot/initrd.img-2.6.22-14-generic

title		Ubuntu 7.10, memtest86+
root		(hd0,7)
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title		Dell Utility Partition
root		(hd0,0)
savedefault
makeactive
chainloader	+1


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda2
title		Microsoft Windows XP Professional
root		(hd0,1)
savedefault
makeactive
chainloader	+1

Can anyone please help? 

This is what I have at the moment in menu.lst

---

### Post by wolfen69 on 2008-01-27
this link [http://ubuntuforums.org/showthread.php?t=442945](http://ubuntuforums.org/showthread.php?t=442945) may help.

---

### Post by cdaringe on 2008-01-27
does grub even show up when you boot?
if not, editing the menu.lst wont get ya too far.
the solution is actually not bad.
boot from your live CD, open a terminal and reinstall grub.
you have to tell it where to install grub, and a few commands to do so.
if you search the forums for "reinstall grub" you should be well on your way back to happy land.
if it still shows up when you boot just doesnt work....hmm. try the above post i suppose!

Good luck. keep us updated.

---

### Post by marchino61 on 2008-01-27
@wolfen69 - I already tried everything I could from that thread before Posting. I also went to Herman's Grub page, which is where I learnt about Super Grub, which has at least meant I can get back into XP.

@cdaringe - I presume Grub is still there - otherwise surely it could not give me the "error 17" message?

---

### Post by polmir on 2008-01-27
> **marchino61 said:**
> ...I can get back into XP.

Take your install Cd winXP. Put in to Cdrom and start winxp install.
With menu start item recover MBR
good luck

<<My Linux is better from my English>>

---

### Post by marchino61 on 2008-01-27
> **polmir said:**
> Take your install Cd winXP. Put in to Cdrom and start winxp install.
With menu start item recover MBR
good luck

<<My Linux is better from my English>>

That's fine for XP, but how do I get back into Ubuntu?

---

### Post by logos34 on 2008-01-27
Paragon messed up ubuntu.  I'd reinstall rather than waste time troubleshooting.

Use gparted on the live cd (system>admin>gnome part editor) to delete sda8 and 9, then reinstall into the empty space.

---

### Post by cdaringe on 2008-01-27
i kindly disagree with the last post. i think its worth the short term stress to figure these things out. helps your problem solving skills...ok, so maybe it helps your googling skills more, but regardless. you learn a lot!

I must have not read the complete post when i first read it. but i remember when i had my first (and last) error 17.  dont remember exactly what i did, but i probably just reinstalled grub.

im going to assume that when you boot from the live cd you can browse to your previous Ubuntu install.  you already said you could.  this is a great sign because that means that the partition is mountable. resizing it didnt goof it up, just goofed the grub parameters up, as you may have expected.

ill help you reinstall grub. it only takes a minute once you open a terminal.  It will also auto-detect your windows install.  so youll be in good shape. im going to borrow some words from wernst.

"Don't forget that this method, as described, puts GRUB back on the MBR (master boot record) of the hard drive instead of in the root parititon. [this is what WE need to do]...

1. Boot from a Live CD, like Ubuntu
2. Open a Terminal. 
3. Type "sudo grub" which makes a GRUB prompt appear.
4. Type "find /boot/grub/stage1". You'll get a response like "(hd0)" or in my case "(hd0,3)". Use whatever your computer spits out for the following lines.
5. Type "root (hd0,3)". [or whatever your comp returned to you in the last step]
6. Type "setup (hd0,3)". This is key. Other instructions say to use "(hd0)", and that's fine if you want to write GRUB to the MBR. If you want to write it to your linux root partition, then you want the number after the comma, such as "(hd0,3)". [you should write yours to the MBR]
7. Type "quit".
8. Restart the system. Remove the bootable CD.
...
-Warr"

if this doesnt fix it, then boot back into windows. i havent used it forever, but im pretty sure that it has a "repair the master boot record" function. use it, then repeat the process i just posted. i know its a lot or restarting and reloading, but hopefully it works after the first go.

Hopefully i didnt ramble TOO much.

---

### Post by polmir on 2008-01-28
[QUOTE= marchino61]That's fine for XP, but how do I get back into Ubuntu?[/QUOTE]

After this operation --- You reinstall grub from liveCD ubuntu

[Red this  all carfully.]("http://users.bigpond.net.au/hermanzone/p15.htm#reinstallgrub")

<<My Linux is better from my English>>

---

