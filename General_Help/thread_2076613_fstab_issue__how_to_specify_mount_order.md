---
title: "fstab issue:  how to specify mount order?"
date: 2012-10-26
forum: General Help
---

### Post by arkanabar on 2012-10-26
I'm not very familiar with the Precise startup & boot process (I'm using a custom DE, based mostly on Madbox 12.04), but I have heard that lots of processes run in parallel in order to speed things up.  And from what comes across my screen (errors complaining "Mount point does not exist"), it looks like sometimes the system is trying to mount my wine partition or my backup partition (both of which are shared among multiple distros on the same machine) into my home partition before it actually mounts my home partition.  With fstab like this, is that possible?  And if it is, what do I do about it?

```
# /etc/fstab: static file system information.
#
# Use 'blkid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda7 during installation
UUID=c40665de-3d1d-4ce5-8bd7-005b68d4eed8 /               ext4    errors=remount-ro 0       1
# /home was on /dev/sda8 during installation
UUID=cc1d15d0-4c64-44f8-b2ec-e359854d31b0 /home           ext4    defaults        0       2
# swap was on /dev/sda5 during installation
UUID=dd7cf35a-0b98-41cc-81cd-d63c41cd20d2 none            swap    sw              0       0
# wine partition hacked in
UUID=21e1374d-9004-4121-9905-8ba76615b706 /home/arky/.wine/drive_c/Programs ext4 defaults 0 2
#backup partition
UUID="447c1372-9cdb-4ebe-8e69-035c029029ea /home/arky/docs  ext3 defaults 0 2
```

---

### Post by dino99 on 2012-10-26
what you need into fstab is: /   /home & swap entries, nothing else
as they use uuid, you need to use the good ones, check them with:

sudo blkid

then edit fstab to make change if needed

gksu gedit /etc/fstab

---

### Post by JKyleOKC on 2012-10-26
Try adding the "noauto" option to the troublesome fstab entry:```
# wine partition hacked in 
UUID=21e1374d-9004-4121-9905-8ba76615b706 /home/arky/.wine/drive_c/Programs ext4 defaults[COLOR=Red],noauto[/COLOR] 0 2 
```This should prevent it from attempting to mount too soon. Then add "mount -a" to the /etc/rc.local file just before the existing "exit 0" line, to remount all drives as the very last action of the boot process.

I don't run wine, so this suggestion is untested, but the "noauto" option is intended specifically to prevent such race conditions during boot...

---

### Post by arkanabar on 2012-10-26
JKyleOKC, that seems to have done the trick!  I forgot the bit in the script the first time around, but I think it will solve everything.  I'll know next reboot.

---

### Post by arkanabar on 2012-10-27
I spoke too soon.  Now those partitions don't mount at all.  I have to do it after I log in.  Which, given there are three disks on my system, involves using "sudo blkid" to find out which is where.  I'd write a script to do it if I had any idea where to put it, how to give it root access, and so on.

---

### Post by arkanabar on 2012-10-27
Further information:  It appears that the "noauto" option in fstab explicitly prevents the partitions from being mounted by "mount -a".  Can I then replace the "mount -a" command in /etc/rc.local shell with something more explicit?  For example: ```
mount -U 21e1374d-9004-4121-9905-8ba76615b706 /home/arky/.wine/drive_c/Programs
```

---

### Post by JKyleOKC on 2012-10-27
Try replacing the "noauto" option with "_netdev" (be sure to include that leading underline) which is supposed to tell the boot process to mount the device only after the network becomes available; the "mount -a" should then work to mount it with no need to look up the UUID. If it fails to mount automatically, a simple "sudo mount -a" from the terminal should mount it after logging in.

I was looking for the _netdev option when I found noauto and failed to read its actions in full detail; sorry about that!!!

---

### Post by JKyleOKC on 2012-10-27
> **arkanabar said:**
> I'd write a script to do it if I had any idea where to put it, how to give it root access, and so on.Where = /etc/rc.local which runs as root so any script that it launches will automatically have root access. Since it runs before your full environment is set up (that happens during your login) any file reference must have full absolute paths. The usual shortcuts such as ~ or $HOME won't work here. However your script can define local variables for its use, such as parsing the result of a command such as /sbin/blkid (note that commands also need their full paths for safety's sake).

However the _netdev option I mentioned in my other reply should make such a script unnecessary. I hope so, anyway...

---

### Post by Morbius1 on 2012-10-27
Might I offer a suggestion?

Go back to JKyleOKC's original idea and add noauto to the fstab entry.

Instead of "mount -a" in rc.local use:
```
mount /home/arky/.wine/drive_c/Programs
```
The system will check fstab to find out if mounting that mount point is defined and it will find it's that UUID number and you should be good to go.

---

### Post by JKyleOKC on 2012-10-27
Thanks for chiming in! Since arky has several to mount, he'll need a command in rc.local for each of them, but this ought to do the trick nicely.

---

### Post by arkanabar on 2012-10-27
since the _netdev option didn't work for me with mount -a in /etc/rc.local, I went and used a mount -U statement for each partition there, copying UUIDs & mountpoints from fstab.  That works just fine.

---

