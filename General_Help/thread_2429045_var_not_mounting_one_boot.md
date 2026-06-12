---
title: "/var not mounting one boot"
date: 2019-10-12
forum: General Help
---

### Post by rsteinmetz70112 on 2019-10-12
I have several system set up generally the same. They run lvm2 over software raid (mdadm). I've used this configuration for years because updating it is too hard and I need the systems up.

After a recent upgrade one of my machines has stopped booting completely. It fails after assembling the arrays and identifying the lvm volumes. It appears to be caused by /var not being mounted. I have a separate /var filesystem because I have had problems with runaway processes filling the logs with stuff and running root out of space since these systems generally operate without supervision for long peroids. It's also the way I learned to do it a long time ago. I generally keep / fairly small.

During the boot process I first get :
```
WARNING: Failed to connect to lvmtad Falling back to device scanning:
Volume group system not found
Cannot Process volume group system
WARNING: Failed to connect to lvmetad Falling back to device scanning:
Volume group system not found
Cannot Process volume group system
WARNING: Failed to connect to lvmetad Falling back to device scanning:
WARNING: Failed to connect to lvmetad Falling back to device scanning:
/dev/mapper/system-root clean: clean ...

```
After investigation is seems /var is not mounting and that is what causes the boot to fail at this point

The problem is I can't figure out why /var is not mounting. The /etc/fstab file looks right 

```
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/           /media/floppy0  auto    rw,user,noauto  0       0
/dev/mapper/system-root /       ext4 defaults 0 1
/dev/mapper/system-var /var   ext4 defaults 0 2
/dev/mapper/system-tmp   /tmp   ext4 defaults 0 2
/dev/mapper/data-files /files ext4 defaults 0 2
/dev/mapper/data-home /home  ext4 defaults 0 2
/dev/system/swap  none swap sw 0 0
```
All of the other file systems mount automatically.
After I log into the Emergency Mode and 
```
# mount /var
```
I can then boot normally.

I can't figure out why it's not mounting.
I'd also like to solve the lvmetad problem

---

### Post by TheFu on 2019-10-13
Is the RAID managed by lvm or is it a separate md[0-9] devices with LVM added on top?

Let's start with gathering some LVM data.
```
sudo pvs  -o +devices
sudo vgs
sudo lvs

```to start.

And of course, /var doesn't need to be fsck'd, correct?

LVM metadata is kept in /etc/lvm/backup.  It is possible to force the data to be wiped and refreshed.  I need to look up the 2 commands. Both are needed, in that order.```

   sudo pvscan --cache
   sudo pvscan 
```

Also, the system log files have some useful data.  **journalctl -b ** should show any LVM boot issues.

I haven't had to touch any mdadm commands in a few years, but how did the last "scrub" go?

---

### Post by rsteinmetz70112 on 2019-10-14
> **TheFu said:**
> 
And of course, /var doesn't need to be fsck'd, correct?


It turns out ```
# fsck /var 
``` while in Emergency Mode solved the problem, I assumed since there was no error and since it mounted manually without comment it was OK. I'm still not sure why it wouldn't mount on boot por why in all of the restarts it didn't do an auto files system check. Of course since /var couldn't be mounted there are no logs.

> Is the RAID managed by lvm or is it a separate md[0-9] devices with LVM added on top?
The raid devices are separate /dev/md1 & /dev/md127
The LVs are links to /dev/dm[0-7]


> I haven't had to touch any mdadm commands in a few years, but how did the last "scrub" go? 
I've recently rebuilt the array with new larger drives and after the first new drive synced with the old one and the other new drives synced with the first new one everything has been working correctly.

---

