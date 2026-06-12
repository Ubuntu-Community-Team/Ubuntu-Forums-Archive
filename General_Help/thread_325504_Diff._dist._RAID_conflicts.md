---
title: "Diff. dist. RAID conflicts?"
date: 2006-12-25
forum: General Help
---

### Post by quad3d@work on 2006-12-25
I have 4 HDs (hda, hdb, sda, sdb). Ubuntu is set up with 3 RAIDs: /boot (/dev/md0; hda1, hdb1, sda1, sdb1), swap (/dev/md1; hda2, hdb2, sda2 sdb2), and / (/dev/md2; hda3, hdb3, sda3, sdb3).

Today I tried to install Arch Linux on RAID as well. It encountered kernel panic... so I tried to reboot into Ubuntu. During boot up it detected Arch Linux's RAID sets as well as md4 and md5 and throws me into single user mode.

Been messing with Arch Linux's RAID setup this whole weekend and I'm tired of looking into solutions. So I booted into Windows and deleted Arch Linux's RAID sets, thinking that Ubuntu wouldn't UDEV md4 and md5 anymore.

Reboot, GRUB into Ubuntu, errors on reading md2... something about can't mount /root partition.

I don't have much to lose so I don't really care about fixing it... my question is... If installing 2 Linux dists. and naming /dev/md0 ~ /dev/md* would it cause any conflict? From this case it looks like it.

So with my original setup I suppose to name my Arch Linux RAID sets to /dev/md4 and /dev/md5 instead of /dev/md0 and /dev/md1? So it wouldn't conflict with Ubuntus'? Thanks.

---

### Post by quad3d@work on 2006-12-26
So I got a little more information from IRC about this solution...

Ubuntu kernel will try to autodtect RAID partitions other than specified in /etc/ config file. Anyone know the method to disable kernel autodetecting other RAID partitions? Thanks.

---

