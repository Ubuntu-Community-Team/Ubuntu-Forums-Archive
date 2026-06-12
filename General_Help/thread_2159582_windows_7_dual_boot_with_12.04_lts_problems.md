---
title: "windows 7 dual boot with 12.04 lts problems"
date: 2013-07-03
forum: General Help
---

### Post by omniaparatus on 2013-07-03
hey guys i tried installing 12.04 on a empty 1.5 tb drive [with my 64 gb kingston drivewindows 7 disconnected]from a storebought install disk and my computer would not boot from dvd/bd/cdom

so next i tried booting from windows saying i needed help booting from cdrom and it gave me the option to dualboot so i tried that. 
it seemed to work and ubuntu works but only if i keep the install disk in the drive.
if  i restart w/o the install disk it says cant find install media or something.

so i check if it did install and ubuntu installer says it is already installed.

so what gives here?

is it installed on hdd or just in ram

---

### Post by efflandt on 2013-07-03
You need to set your BIOS to boot the 1.5 TB drive. The mbr of that drive is undoubtedly where the grub boot loader is if you had your normal boot drive disconnected during install. Although grub should be able to find partitions by UUID, there have been times when it seems to base that on the physical disks, so it might have an issue trying to find things that were on the primary (only) drive during install, which are now on the secondary drive.

But first just see if changing CMOS setup to boot your 1.5 TB drive instead of your 64 GB drive works.  Then run "sudo update-grub", so it will find Windows and also be able to boot that from there.

I sort of do that. Windows and one Ubuntu is on my 1 TB primary drive, but I boot everything from grub on my secondary 80 GB SSD which has another Ubuntu version. I did not disconnect any drives during install, I just made sure that I put grub on the drive I wanted it on. The first drive just has a regular Windows mbr because there was a time when some Windows programs (like Dell DataSafe) would store data in what they "thought" was an unused part of the mbr (which was actually being used by larger grub2). But I think grub has now isolated those areas of the mbr where known Windows programs are known to store data.

---

