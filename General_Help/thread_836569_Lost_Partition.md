---
title: "Lost Partition"
date: 2008-06-21
forum: General Help
---

### Post by T75OyyU5 on 2008-06-21
hi, 

my PC was dual boot with WinXP and Ubuntu. I decided to uninstall Ubuntu so I fired up Partition Magic in Windows and deleted the linux partition. I then resized the windows partition to take the space left by deleting the linux partition. 

On reboot, I received a GRUB error (22 I think). 

I started to look for help on the web and found some information about fixing the MBR from ubuntu (I have a LiveCD of Ubuntu). 

Nothing worked and to make matters worse, the MBR/Partition table must be corrupted because it is showing the hard drive as unformatted with no partitions!!! 

I have some valuable data I need to recover before I can reinstall Windows from a (rather old) backup. 

Can anyone help? 

R

---

### Post by logos34 on 2008-06-21
You can't fix grub on the mbr from the live cd because you deleted ubuntu root! -- it needs files on that partition.

Get the [Super Grub Disk]("http://supergrub.forjamari.linex.org/") and restore the windows bootloader.  

If that doesn't help, you might want to check out TestDisk to fix the partition table. It's available on the [Parted Magic]("http://partedmagic.com/") rescue cd. Or use it from the ubuntu cd as described [here]("http://ubuntuforums.org/showpost.php?p=5233913&postcount=5").

---

### Post by smo0th on 2008-06-21
you could try your windoze installation cd in recovery mode to fix the MBR,  you could also try logos34's advice.

---

