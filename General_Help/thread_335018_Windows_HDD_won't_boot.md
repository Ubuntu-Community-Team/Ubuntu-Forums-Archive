---
title: "Windows HDD won't boot"
date: 2007-01-09
forum: General Help
---

### Post by beetee2 on 2007-01-09
I am a linux nub, and am experiencing some problems w/ my Windows XP boot, and if it weren't for having Ubuntu installed on my 2nd HDD I'd be SOL right now.  However, my pc has 2 hard drives, one w/ exclusively Windows XP Home edition, the other one w/ Ubuntu Linux installed and formatted into 4 partitions, now onto the problem...  I was downloading and installed the World of Warcraft patch today, and it locked up at 71%, so I tried to ctrl + alt + del and restart, but to no avail, so I powered down my pc.  When my computer boots it gets to the GRUB boot loader, and has Ubuntu, and Microsoft Windows XP listed.  When I select Microsoft Windows XP I get this screen shortly thereafter:

Booting 'Microsoft Windows XP Home Edition'

root (hd0,0)
   Filesystem type unknown, partition type 0x7
savedefault
makeactive
chainloader +1

A disk read error occurred.

I did a little research and found that it is commonplace that the partitions on the HD may have been corrupted?  I did run a "sudo fdisk -l" and this is the output:

Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       19456   156280288+   7  HPFS/NTFS

Disk /dev/sdb: 200.0 GB, 200049647616 bytes
255 heads, 63 sectors/track, 24321 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1       21130   169726693+  83  Linux
/dev/sdb2           21131       24321    25631707+   5  Extended
/dev/sdb5           23565       24321     6080571   82  Linux swap / Solaris
/dev/sdb6           21131       23564    19551042    b  W95 FAT32

Partition table entries are not in disk order

 I'm not really sure exactly what this means, where to go with this or what to do, I'm actually quite lost, and I have a lot of important stuff on my windows hard drive (apparent mistake) that I cannot afford to lose!  If anyone has any assistance, or how I can fix my Windows XP HDD without losing everything through my Linux Install plz let me know!  Thank you for your time!

---

### Post by mistypotato on 2007-01-09
Well, this IS a Linux forum...

But...

I won't say "shame on you for not backing up your valuable data" because you're probably already thinking that ;) 

You might try the Windows FixMBR command from the command prompt.
Also, I would disconnect the Linux HD from the system temporarily (IDE cable and power connector) until
you sort things out.   Since you installed on separate HD's, they have nothing to do with each other except
the MBR of the Windows drive may have an entry for the Linux drive.
Sometimes, you just make things worse.  Your data is still likely there and you could connect the Windows drive
as a SLAVE drive in another system to get your data.  But the more you do, the less chance you have to recover your data.

It sounds like a Master Boot Record Problem

Unless you accidentally deleted or reconfigured partitions.

---

### Post by beetee2 on 2007-01-09
Thank you for your reply.  I posted here because I've lurked for quite some time and I know there are several very knowlesgeable people here, and I was hoping there would be a way to USE Ubuntu to FIX Windows... You aren't aware of any means that I could use my Linux installation to fix my Windows XP Problem?  Or at least find out what the problem IS?

For right now I'll disconnect my Ubunutu HDD and run a 'fixmbr \Device\HardDisk0' in the Recovery Console.

---

### Post by mistypotato on 2007-01-09
You cannot by any means, use your Linux OS to Repair your Windows OS.

You need to stop.....relax....and not do anything without great care.

First, you need to assess how important your Windows data really is.

If it's "Critical", you should get help.

Otherwise, you could start over.

ReInstalling Windows (without reformatting) will repair your Windows system
USUALLY without data loss.   I don't see from your initial post where you compromised
the data on the Windows drive....just maybe botched the MBR.

But again, you might want to get professional help if you have critical data on the Windows drive.

---

