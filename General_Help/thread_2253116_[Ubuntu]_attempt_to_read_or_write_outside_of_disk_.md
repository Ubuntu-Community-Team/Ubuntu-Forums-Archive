---
title: "[Ubuntu] attempt to read or write outside of disk 'hd0'"
date: 2014-11-17
forum: General Help
---

### Post by zinv86 on 2014-11-17
Hello, so recently i ran into an issue after a fresh install of 14.04.1, and an upgrade to 14.10. After a crash in chrome one day that results in a need for a hard reboot, i ran into the following error:
attempt to read or write outside of disk 'hd0'

I atttempted to run rescue, ran an fsck and everything worked as normal again. Just to make sure rebooted one more time same issue appeared again. 

I then did a fresh install and upgrade again, and ran into the same issue.

Next, i tried to do a fresh install of 14.04.1, and not upgrade, installed amd drivers as well but previously had not. Currently was running okay for a few days. Then yesterday i reboot, and see the above error again:

attempt to read or write outside of disk 'hd0'

I boot into recovery mode from grub, select the grub option to update grub, then continue to boot and everything booted okay.

Im scared to reboot now because i know i will see the same error again.

Also another thing i noticed for the drive that were booting from when running fdisk on it:

The device presents a logical sector size that is smaller than
the physical sector size. Aligning to a physical sector (or optimal
I/O) size boundary is recommended, or performance may be impacted.


Command (m for help): p


Disk /dev/sda: 2000.4 GB, 2000398934016 bytes
255 heads, 63 sectors/track, 243201 cylinders, total 3907029168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes
Disk identifier: 0x1fff9afb


   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *        2048  3783655423  1891826688    7  HPFS/NTFS/exFAT
/dev/sda2      3783655424  3907028991    61686784   83  Linux


Command (m for help):

If any one has any suggestions please let me know or if any additional logs/files will be helpful ill be available.

Thank you,

---

### Post by zinv86 on 2014-11-17
So just an update for anyone looking into something similar. Currently i attempted to do the following which i saw in another thread regarding similar error:
[COLOR=#000000]sudo mv /initrd.img /initrd.img.bak[/COLOR]
[COLOR=#000000]sudo dpkg --configure -a[/COLOR]
[COLOR=#000000]sudo apt-get install --reinstall linux-image-3.13.0-39-generic

[/COLOR]After rebooting the error below did not re-occur:

attempt to read or write outside of disk 'hd0'

Im still afraid to attempt rebooting again atm, as I am doing all this remotely currently. Once i get home after work again I will try rebooting again and see what the results are. If i receive the same error, my next step will be to delete the large NTFS partition on the drive in question, /dev/sda. I will then recreate a seperate boot partition at the beginning of the drive and see if that may be the potential causeo this, though i had not experienced this issue previously, and i have had 14.04 installed on in for quite some time. It did seem to originate once i installed the latest kernel in 14.10, but unsure of what version it was believe it ended in a -26 but not sure. If anyone has any additional input or information on what may be causing this please feel free to let me know.

---

### Post by oldfred on 2014-11-17
Usually that error is related to last partition ending beyond the last sector of drive. But yours looks ok.
Or perhaps sectors not starting on 4K boundries, but yours do.

Info, but yours looks ok to me.
 First, understand that most partitioning tools have moved to a policy of aligning partitions on 1 MiB (2048-sector) boundaries as a way of improving performance with some types of arrays and some types of new hard disks (those with 4096-byte physical sectors). See article by srs5694:
[http://www.ibm.com/developerworks/linux/library/l-4kb-sector-disks/](http://www.ibm.com/developerworks/linux/library/l-4kb-sector-disks/)
Post on 8-sector boundaries alignment by srs5694
[http://ubuntuforums.org/showthread.php?t=1685666](http://ubuntuforums.org/showthread.php?t=1685666)
it's 8-sector (4096-byte) alignment
[http://ubuntuforums.org/showthread.php?t=1768635](http://ubuntuforums.org/showthread.php?t=1768635)
Alignment issues on 4K drives
[http://ubuntuforums.org/showthread.php?t=1635018](http://ubuntuforums.org/showthread.php?t=1635018)

But when you said hard reset, did you remember the elephants?
      
 Never force shutdown your system. Use Alt+SysRq R-E-I-S-U-B instead. (For newer laptops they don't bother adding the SysRq print to the key, but it's the same as the PrtScr key)

   Holding down Alt and SysRq (which is the Print Screen key) while slowly typing REISUB
R-E-I-S-U-B to force shutdown
A good way to remember it is.
Raising Skinny Elephants Is Utterly Boring ...or
Reboot System Even If Ultimately Broken ...LOL.
[xhttp://kember.net/articles/reisub-the-gentle-linux-restart/](xhttp://kember.net/articles/reisub-the-gentle-linux-restart/)
[http://ubuntuforums.org/showthread.php?t=1509765&p=12543274#post12543274](http://ubuntuforums.org/showthread.php?t=1509765&p=12543274#post12543274)

If you force shutdown or have an abnormal shutdown, you may have to run e2fsck to repair file system and/or chkdsk from Windows for NTFS file system.

---

### Post by zinv86 on 2014-11-17
Thank you for the inpurt oldfred, I had gone ahead and read all those threads already, which is what i thought was originally the issue. But then realized i do have the 1mb prior to first partition to align them correctly i believe. Also, the first time the error occured i did run an fsck. This resolved it till the next reboot where the error appeared again. I also do believe any additional time ive run an fsck since then from the Recovery mode, the system will boot correctly with out the error as well. Im gonna do some more testing regarding this once i have time and am next to the machine. If i still am getting the error ill see if possible trying to correct the alignment so that Sector size (logical/physical) shows 4096/4096. it may have been that i originally created the 1.7TB parition in Windows but really cant remember anymore.

---

### Post by oldfred on 2014-11-17
Because you start at sector 2048, you do have the 1MB at beginning of drive. Starting at sector 2048 is now the standard for compatibility with 4K drives and SSDs.

Did you run fsck or e2fsck. I think just fsck checks if flag for repair is set and only then runs the file check.
       #From liveDVD/Flash so everything is unmounted,swap off if necessary, change example shown with partition sdb1 to your partition(s)
#e2fsck is used to check the ext2/ext3/ext4 family of file systems. -p trys fixes where response not required
sudo e2fsck -C0 -p -f -v /dev/sdb1
#if errors: -y auto answers yes for fixes needing response, also see man e2fsck
sudo e2fsck -f -y -v /dev/sdb1

---

### Post by zinv86 on 2014-11-17
I will take a look at running e2fsck, i only attempted the fsck option from the recovery mode. Also, i have gone ahead and attempted rebooting the box in question multiple times through the day today, and it has yet to experience the failure to boot as previously. So im thinking maybe there was an issue with the previous version of the kernel, or maybe the initrd.img was corrupted from install. Though that wouldnt make to much sense as to why the error occured as well in 14.10.

---

