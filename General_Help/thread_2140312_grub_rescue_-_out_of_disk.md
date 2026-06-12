---
title: "grub rescue - out of disk"
date: 2013-04-29
forum: General Help
---

### Post by alanfolsom on 2013-04-29
I have a server running 12.04 (single boot) that has been operational for quite some time, running pretty much unattended.  Today I discovered it unresponsive, and after trying to reboot got "Error: Out of Disk" followed by a "Grub Rescue" prompt.

Trying to boot from a 12.04 installation disk gives a long pause, followd by "timeout '/sbin/blkid -o udev -p /dev/sda' and then several 
timeout:killing '/sbin/blkid -o udev -p /dev/sda' messages.

I eventually get to the ubuntu booting box, which never proceeds (just the rotating lights).

Any suggestions as to how to fix this problem?  Wiping the system and restarting would be a last resort, plus I'm confused as to why I can't boot from the installation CD.

Thanks.  I have a lot of generic computer experience, but am an absolute beginner when it comes to Ubuntu.

ALF

---

### Post by alanfolsom on 2013-04-29
For what it's worth, leaving the installation running for a very long time eventually boots, after showing more timeout messages for sda1 and sda5.  I'm not sure what to try now, though.  I can run under "Try Uunutu".  Are there rescue options to explore?

---

### Post by ARooster on 2013-04-29
I'd suggest "Try Ubuntu" and attempt to back up the data to an external hard drive. Then no matter what happens at least you've got the data.

You might want to try this option, given in the [Community help Wiki on the Ubuntu site]("https://help.ubuntu.com/community/Boot-Repair").

---

### Post by oldfred on 2013-04-29
From a desktop I use Disks or Disk Utility to check Smart status of a drive.
I only know enough that passed is good and anything else is a new drive.

There are command line versions.
The smartmontools package contains two utility programs (smartctl and smartd)
to control and monitor storage systems using the Self-Monitoring, Analysis and
Reporting Technology System (S.M.A.R.T.) built into most modern ATA and SCSI
hard disks.

You may need a full e2fsck, if drive is otherwise ok?

       #From liveCD so everything is unmounted,swap off if necessary, change example shown with partition sdb1 to your partition(s)
#e2fsck is used to check the ext2/ext3/ext4 family of file systems. -p trys fixes where response not required
sudo e2fsck -C0 -p -f -v /dev/sdb1
#if errors: -y auto answers yes for fixes needing response see man e2fsck
sudo e2fsck -f -y -v /dev/sdb1

---

