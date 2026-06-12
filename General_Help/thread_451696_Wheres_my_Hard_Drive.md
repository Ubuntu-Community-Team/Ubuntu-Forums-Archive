---
title: "Wheres my Hard Drive?"
date: 2007-05-22
forum: General Help
---

### Post by indigenous71 on 2007-05-22
Well I've just installed Ubuntu (7.04) and while I was installing I was told to change the size of one of the default partitions (that had been created by the manufacturer). I adjusted it so there were no partitions and installed, I got two error messages about linux being unable to get information about the two drives until reboot. I installed and rebooted and was very surprised to see an options list as to which operating system to boot. I booted Ubuntu Generic (the other two Ubuntu options were command line and recovery) and then the system seemed to scan one of the drives/partitions and it failed, the system rebooted again and Ubuntu loaded up fine. However when I click 'Computer' in the Places menu it shows me the CD Drive, PQService and Filesystem. I presume that Filesystem is the main drive or folder but it cannot find the size of the drive. I worried that I've lost half of my hard drive because of the partitions, is there anyway that I can find out using an online applet or something I can download.

All help very much appreciated;).

---

### Post by benmoreassynt on 2007-05-22
At command line you can type

df -h

Which will give you size of all mounted drives in MBs and KBs. Mine is /dev/sda1

or use the Disk Useage Analyzer (not sure where it is in Gnome, but it's in Utilities in KDE). I believe it's a default Ubuntu application. There is also the Gnome Partition Editor for editing allocations without reinstallation or anything horrible. These will both be in the systems menu somewhere in Gnome I suppose.

---

