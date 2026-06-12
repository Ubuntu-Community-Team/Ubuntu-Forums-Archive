---
title: "How can I back up my recovery partition?"
date: 2007-12-14
forum: General Help
---

### Post by Bright Carver on 2007-12-14
Hi

I have a Packard Bell desktop with WinXP I'd like to dual-boot with Ubuntu.  It has a recovery partition stuck to the MBR, so I can't really set up GRUB without destroying my chances of recovering XP if something messes up.  Also, I can burn a set of recovery CD's from the Packard Bell Smart Restore program, but only once.  If I get a bad burn, I'm screwed.

Is there a way of backing up my hidden recovery partition?

My computer has:
180Gb HD (about 200Gb really)
1024Mb RAM
Ehernet internet
CD/DVD drive/burner
USB pendrive
10 spare DVD-R's

It doesn't have:
floppy drive
external HD
USB booting BIOS

I think the idea is to make a FAT partition on my Windows drive for sharing, boot into liveCD, copy the data from the recovery partition, save it to the shared partition, reboot into Windows and burn to DVD('s?), but I don't have a clue how to do this.

Any help would really be fantastic.

Thanks

Karl

---

### Post by oscarsfriend on 2007-12-14
You should be able to use dd (command run from a terminal) to make an image of the partition.  Don't ask me how, I've never tried it.  Search through the forums and you will likely find out how.

---

### Post by geirha on 2007-12-14
The MBR is not a partition and is far too small to be able to contain one. My guess is you have a hidden fat16/fat32 partition at the beginning of the harddrive. If you just leave it alone there shouldn't be a problem. Could you post the output of this? ```
sudo fdisk -l
``` (run it from the ubuntu cd)

---

### Post by Bright Carver on 2007-12-14
Yeah, I've read about dd on my many searches, but I don't know enough about it all to use it with confidence!

---

### Post by Bright Carver on 2007-12-14
Hi :)

The MBR contains the emergency restore options that open the hidden partition in the case of a broken OS, and reinstall Windows with all my drivers and the awful Packard Bell wallpaper.  In the absence of an alternative medium to place my bootloader, I'd rather back up the MBR and recovery partition then just overwrite my MBR with GRUB.

It's the scary partitioning and dd-ing I need help with!

Will post up the results when I've burnt a CD...

Thanks

Karl

---

### Post by geirha on 2007-12-14
Well, backing up the MBR is easy, you just copy the first 512 bytes of the harddrive ```
sudo dd if=/dev/sda of=mbr.backup count=1
``` (assuming your harddrive is connected to /dev/sda). Restoring is the same command just with the arguments of if= and of= switched around.

Backing up the partition would be to just mount it and archive its content with tar or zip or whatever you prefer. You can also use dd to back up the entire filesystem, though in order to restore it you should make sure the partition to restore it to is the same size. (The partition is probably very small, so removing it shouldn't be necessary to install ubuntu.) 
```
sudo dd if=/dev/sda1 of=recovery.backup
```

---

### Post by psusi on 2007-12-14
Yea, just backup the MBR with dd if you are worried, and ignore the hidden restore partition.

---

### Post by Joshua on 2007-12-14
I think know what your talking about because my recent laptop has a similar-sounding setup.  The first thing I'd do is complain to the company that they don't send real recovery disks with new computers anymore.  The second thing I'd do is find a forum for your specific computer and ask around if anyone has done it.

For mine, it was an Averatec, and there was a bit of software (I think it was Phoenix Recover Pro, or something like that) that you could activate on boot because it was part of the MBR.  That would go into a hidden partition and rebuild the factory shipped software.  When you used it, it was like brand new where you have to go through Windows setup and everything.  Through an Averatec users forum I found someone who had developed a live-cd type of Linux distribution that would automatically back up everything from the recover partion to a DVD.  Once you installed Linux, you lost the MBR software, and you would lose the hidden partition when you tried to recover to Windows.

Basically, as shipped there were seveal Gigabytes of space that were unusable because they contained the hidden partition and an image of the factory shipped software.  I backed everything up with the live-cd, and installed Ubuntu.  This gave me one partition for Windows and one partition for Ubuntu, but the recover software no longer worked as there was no recover partition, and the MBR now had GRUB.  I actually got warnings when I booted into Windows that the recover software had changed and it would offer to fix it (you wouldn't want to do that because it would make Ubuntu unbootable).

When I used the recover DVD that I made, it put everything back to the way it was, but without the recover partition (you now had the extra space instead) - MBR was back to as-shipped state, too.  I think the software that came with the computer could have recreated the recover partition if I wanted, but it had a time limit (only a trial offer) and I never used it.

I suspect that the live-CD could be used on any similar setup.  I'll see if I can find it when I get home, and post a link if I do.

---

### Post by geirha on 2007-12-14
BTW, having thought a little bit more about this, I doubt the MBR contains anything related to the recovery partition. If it did, it would be removed by windows if you ever installed it manually. It's more likely you access the recovery partition from the BIOS by pressing some Fn-key to access a menu before the OS-boot. This at least used to be the common way of doing it on laptops a few years ago (probably still is).

---

### Post by psusi on 2007-12-14
Windows won't mess with the MBR boot code if there is an existing valid MBR, so it is common for such recovery utilities to put their own boot code in the MBR that boots the recovery partition instead of the active windows partition.

---

### Post by Bright Carver on 2007-12-15
I've never installed Windows manually on this machine.  I've needed a reinstall twice on this machine since I bought it, and both times just used the SmartRestore program.

Searching the Packard Bell forums taught me I shouldn't just rewrite the MBR with GRUB.  Since I don't have a floppy drive, and can't boot from USB, I think I should back it up first.

It might be the case that I can just back up the MBR (then I could just copy it to a pendrive!).  I'm going to try that first in my LiveCD.

---

### Post by Bright Carver on 2007-12-15
Here's the output of fdisk

```
Disk /dev/hda: 200.0 GB, 200049647616 bytes
255 heads, 63 sectors/track, 24321 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xace22e9e

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1               1         765     6144831   1c  Hidden W95 FAT32 (LBA)
/dev/hda2   *         766       24320   189205537+   7  HPFS/NTFS

Disk /dev/sda: 66 MB, 66240512 bytes
4 heads, 32 sectors/track, 1010 cylinders
Units = cylinders of 128 * 512 = 65536 bytes
Disk identifier: 0x00000000

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        1011       64672    6  FAT16
Partition 1 has different physical/logical endings:
     phys=(1023, 3, 32) logical=(1010, 2, 32)
```

Thanks!

---

### Post by Bright Carver on 2007-12-15
If I do this:

```
sudo dd if=/dev/sda of=mbr.backup count=1
```

Where does the data end up? I think my HD is hd0 and hd1, and my USB drive is a sd0.  I've never dd'd before!  Is it like a clipboard thing?  Saving my MBR to the pendrive should be viable.

Also, is it the first chunk of the hidden partition or the Windows one?

Thanks for all your help, I think I might be actually getting somewhere!

Karl

---

### Post by geirha on 2007-12-15
> **Bright Carver said:**
> If I do this:

```
sudo dd if=/dev/sda of=mbr.backup count=1
```

Where does the data end up? I think my HD is hd0 and hd1, and my USB drive is a sd0.  I've never dd'd before!  Is it like a clipboard thing?  Saving my MBR to the pendrive should be viable.

Also, is it the first chunk of the hidden partition or the Windows one?

Thanks for all your help, I think I might be actually getting somewhere!

Karl

Ok, so the drive with the recovery partition is /dev/hda, then the dd-line would be:
```
sudo dd if=/dev/hda of=mbr.backup count=1
```
The command copies 1 block (512 bytes) from the start of the harddrive, and stores it to the file pointed to by "of=", which in this case is mbr.backup in the directory you're running the command from. The first 512 bytes of the harddrive is what is called the MBR.

---

### Post by psusi on 2007-12-15
You appear to have two physical disk drives, one of which is only 60 mb.  Is that correct?

---

### Post by santaslittlehelper on 2007-12-15
I have setup dual boot on both a HP Pavilion and an Acer with the same "recovery partition" scheme. 

In both cases I have been able to restore the mbr with Super Grub  - [http://users.bigpond.net.au/hermanzone/SuperGrubDiskPage.html](http://users.bigpond.net.au/hermanzone/SuperGrubDiskPage.html) - also in both cases I have been able to boot the "recovery partition" via grub. 
[http://gentoo-wiki.com/HOWTO_Gentoo_on_laptops](http://gentoo-wiki.com/HOWTO_Gentoo_on_laptops)
If either of those options would work for you is hard to say but I would think so.
Anyway I would recommend you make a boot partition.

If you try to create a backup of the partition with “dd” I would be curious to know how it works out since I never gave it a try. 

Hope it all works out.

---

### Post by Bright Carver on 2007-12-16
psusi:
Yes, that's my pendrive!  Not much, but enough to stick my MBR on...

santaslittlehelper:
Great!  I've got some reading to do.  That Gentoo wiki seems to be exactly what I was looking for, but I think I need to read up on Super GRUB!  Before I do, can you tell me offhand if the GRUB CD has to stay in the drive for the whole session, or can it be removed when everything has finished loading?

The Super GRUB CD seems to be the least intrusive, if it can be removed, I can ignore the MBR, ignore the recovery partition and just boot Linux from a CD when I need to.

Great stuff, guys!

---

### Post by santaslittlehelper on 2007-12-16
Hi
You should think of Super GRUB as a recovery disk (it's just a ~4 MB image) that you can boot from to fix you're Windows MBR and restore the ability to use recovery, in case you ever what to completely remove Linux. Of course it's only needed if you decide not to create a recovery DVD yourself.

 I can give you an example here from a HP Pavilion. 
 
```
fdisk -l

    Device Boot     Start         End      Blocks   Id  System
/dev/sda1               1         594     4490608+   b  W95 FAT32
/dev/sda2   *         595       18385   134499960    7  HPFS/NTFS
/dev/sda3           18386       25841    56367360    f  w95 Extended (LBA)
/dev/sda5           19619       19755     1035688+  82  Linux swap / Solaris
/dev/sda6           19756       25444    43008808+  83  Linux
/dev/sda7           25445       25841     3001288+   b  W95 FAT32
/dev/sda8           18386       18405      151137   83  Linux
/dev/sda9           18406       19618     9170248+  83  Linux
```

/dev/sda1 = recovery partition
/dev/sda2 = windows
/dev/sda3 = extented partition
/dev/sda8 = /boot
/dev/sda6 = /
/dev/sda5 = swap
/dev/sda9 = /home
/dev/sda7 = FAT32

```
menu.lst

## ## End Default Options ##

title		Ubuntu 7.10, kernel 2.6.22-14-generic
root		(hd0,7)
kernel		/vmlinuz-2.6.22-14-generic root=UUID=370495e5-5848-4e69-9e75-2a27354ca5cb ro quiet splash
initrd		/initrd.img-2.6.22-14-generic
quiet

title		Ubuntu 7.10, kernel 2.6.22-14-generic (recovery mode)
root		(hd0,7)
kernel		/vmlinuz-2.6.22-14-generic root=UUID=370495e5-5848-4e69-9e75-2a27354ca5cb ro single
initrd		/initrd.img-2.6.22-14-generic

title		Ubuntu 7.10, memtest86+
root		(hd0,7)
kernel		/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root

# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda2
title		Windows XP
root		(hd0,1)
savedefault
makeactive
chainloader	+1

# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title		Windows Rescue Partition
root		(hd0,0)
savedefault
makeactive
chainloader	+1
```

In the case of the Acer laptop GRUB used "rootnoverify" in the case of the HP Pavilion GRUB defaulted to this (with the exception of naming the Rescue Partition) and it works.
As said in both cases you could boot into you're "recovery partition" from the GRUB menu and reinstall Windows. 

Again though, if all these partition schemes work more or less the same I just don't know the same goes for if Super GRUB would work for you.

---

### Post by Bright Carver on 2007-12-17
Thanks :)

Here's my final plan then:

1. Boot up a LiveCD
2. Back up MBR to pendrive
3. Create FAT shared partition on HD
4. Back up recovery partition to FAT partition
5. Install Ubuntu to HD
6. Boot up Ubuntu from HD
7. Store backup of recovery partition on DVD('s?)
8. Boot up Windows
9. Burn Packard Bell Windows Master Recovery CD's

Cool.  Then I'll have seperate backups of MBR, recovery partition and my PB recovery CD's. After that, who knows?  Maybe I'll reformat the drive and free up the space from the hidden partition...

The idea is to keep using Windows for everything, and then when we know whether Linux can be tweaked to do everything - including USB printing and Firewire camcorder uploads - to make the switch.

Saying that, during the last crash, my girlfriend was delighted at the LiveCD.  That's all she wants now.  Just a LiveCD with OpenOffice and Firefox.  And a pendrive.  She says she wouldn't mind a PC with no HD and 2 CD drives :)

Anyway, I'm rambling.

Does the above plan seem viable?  If anybody can see any horrible headaches up ahead, could you let me know as soon as possible as I'm wanting to get stuck into this straight away.

Thanks again for the help...

Karl

---

### Post by santaslittlehelper on 2007-12-17
As for all the backing up I can't tell you never been that careful myself :D
Let us know how it turns out and good luck.

---

