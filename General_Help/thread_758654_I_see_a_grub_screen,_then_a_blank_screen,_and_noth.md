---
title: "I see a grub screen, then a blank screen, and nothing happens"
date: 2008-04-18
forum: General Help
---

### Post by sadohert on 2008-04-18
The help I'm hoping to get is pointers on where I can look on my installed filesystem (that I have mounted through the Live CD) to figure out what is going wrong with my machine when it boots up.  Log files?  Xorg debugging?  Try safe mode this, CLI mode that.  Obviously if someone knows exactly whats goign on I'll take that too ;).

Thanks in advance.

Here's the story (short as I could make it without skipping details)

-Had to reinstall Ubuntu because I screwed up the boot partition while trying to be cheaky with "parted" and move my home directory to another RAIDed partition (from the boot partition)
-I had already created the "new" home on the RAID, ready to be mounted, so during install I just put "/" on a smaller partition (wanted to use the remaing space for something else), and made a swap partition
-Install is fine... so I go into Ubuntu, change /etc/fstab to have an entry for mounting that RAIDed filesystem to /home (after I moved the default /home directory to /home_old)... mount the home drive, and everything seems just fine.  Home dirs are behaving correctly... all is good.
-Hook up to the net and download and install all the updates (200MB or I believe)
-Fixed a bug [BUG HERE]("https://bugs.launchpad.net/ubuntu/gutsy/+source/ubiquity/+bug/150930") by changing my usplash.conf resolution to 1680x1050 (my screens max res)

Everything seemed all fine.  Then I rebooted, and all I got was grub, then a blank screen.  Computer is running fine, but ubuntu never boots up.

---

### Post by sadohert on 2008-04-18
Okay... so I think I found the culprit.

Restarted the computer and pressed "ESC" at the Grub screen so I could go into "Safe" mode.  The issue came up when fsck was running.  It told me to look in "/var/log/fsck/checkfs" and I got the message down below.

```
Log of fsck -C -R -A -a
Fri Apr 18 09:04:00 2008

fsck 1.40.2 (12-Jul-2007)
/dev/md1: The filesystem size (according to the superblock) is 24436873 blocks
The physical size of the device is 24436848 blocks
Either the superblock or the partition table is likely to be corrupt!


/dev/md1: UNEXPECTED INCONSISTENCY; RUN fsck MANUALLY.
  (i.e., without -a or -p options)
fsck died with exit status 4

Fri Apr 18 09:04:00 2008
----------------

```

So, /dev/md1 is the RAID device I created using "mdadm".  I had created it during the original install using the --create option, but when I screwed up the OS partition and reinstalled, I issued the "assemble" command to rebuild the array.  I'm wondering if something was screwed up somewhere in that process.

Could I just maybe re-run mdadm on /dev/md1 and maybe "resize" the filesystem area so it is the same size as the physical partition?  What is a "superblock"?  Is this somethign mdadm would have written to to signal to the OS the size of the filesystem?

---

