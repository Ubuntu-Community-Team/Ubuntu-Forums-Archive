---
title: "Probs adding 2nd CDROM or DVD drive..."
date: 2007-08-19
forum: General Help
---

### Post by mikey5555 on 2007-08-19
Hi folks...
Been using UBUNTU 7.04 for a few weeks, just playing and experimenting.  Originally the PC had 1 IDE hard drive and 1 CDROM drive.  I also created and implimented a RAID5 array to use as  a storage area for large files and backups.  
Now I want to add a sony 710A DVD-R/RW dvd/cd burner to the system.  I installed the DVD, connected it to the 2nd IDE bus as a slave to the CDROM drive.  Now it seems I cannot mount either the CD-ROM nor the DVD-R/RW.  Looking into fstab, I find the following:

[I]mike@mike-ubuntu:/etc$ more fstab
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/hda1
UUID=eaab1b24-6b26-4018-ba3c-10f30e52d1d5 /               ext3    defaults,error
s=remount-ro 0       1
# /dev/hda5
UUID=19003608-8941-40ef-82f2-85afc9c7541d none            swap    sw            
  0       0
/dev/cdrom      /media/cdrom0   udf,iso9660 user,auto     0       0
/dev/md0        /media/raid     auto    defaults        0       10[/I]


In the /dev folder, I fine these links for the CDROM and DVD drives:

lrwxrwxrwx 1 root root           4 2007-08-19 11:11 cdrom -> scd0
lrwxrwxrwx 1 root root           4 2007-08-19 11:11 cdrw -> scd0

lrwxrwxrwx 1 root root           4 2007-08-19 11:11 dvd -> scd0
lrwxrwxrwx 1 root root           4 2007-08-19 11:11 dvdrw -> scd0

lrwxrwxrwx 1 root root           4 2007-08-19 11:11 sr0 -> scd0
 

I'm sure there needs to be an entry for the DVD drive but I am unsure just what would be the best way to solve this.  Can Ubuntu recognize and configure this 2 drive (DVD) or is it necessary to create it manually?  Feeling really duuuumb at this point, especially after having successfully created a RAID5 array........

Anyway, should someone feel up to schooling a noob today, I'd appreciate it immensely...

mikey5555

---

### Post by mikey5555 on 2007-08-21
I finally figured this one out:  UBUNTU, apparently, has the ability to recognize and implement, at least in this case, new hardware automatically!  I tried the DVD+-R/RW drive in another machine running Windoze and discovered the drive is faulty - Vista would not even acknowledge it's existence, even though it is detected correctly by BIOS in BOTH Vista machine and the UBUNTU machine.  Bought new DVD+-R/RW and installed into UBUNTU machine, rebooted, and SHAZAM it mounts and reads DVDs and CDs.   

mikey5555

---

