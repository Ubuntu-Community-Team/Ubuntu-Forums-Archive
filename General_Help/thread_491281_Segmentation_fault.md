---
title: "Segmentation fault"
date: 2007-07-03
forum: General Help
---

### Post by afbase on 2007-07-03
In CLI, I type ```
df
```
all i get is
> Segmentation fault


i have two hard drives, but only one is showing in fstab:
```

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/sda1       /               ext3    defaults,errors=remount-ro,usrquota,grpquota 0       1
/dev/sda5       none            swap    sw              0       0
/dev/hdd        /media/cdrom0   udf,iso9660 user,noauto     0       0



```


however my mtab shows that missing hard drive i want shown, on the very last line:

```

/dev/sda1 / ext3 rw,errors=remount-ro,usrquota,grpquota 0 0
proc /proc proc rw 0 0
/sys /sys sysfs rw 0 0
varrun /var/run tmpfs rw 0 0
varlock /var/lock tmpfs rw 0 0
procbususb /proc/bus/usb usbfs rw 0 0
udev /dev tmpfs rw 0 0
devpts /dev/pts devpts rw,gid=5,mode=620 0 0
devshm /dev/shm tmpfs rw 0 0
lrm /lib/modules/2.6.15-27-386/volatile tmpfs rw 0 0
/dev/hdd1 /home/clinton/hdd1 reiserfs rw 0 0

```

How would i remount my hard drive, "/dev/hdd1", again so it no longer has a segmentation fault in CLI?

---

### Post by afbase on 2007-07-03
any ideas?????

---

### Post by pjkoczan on 2007-07-03
> **afbase said:**
> In CLI, I type ```
df
```
all i get is



i have two hard drives, but only one is showing in fstab:
```

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/sda1       /               ext3    defaults,errors=remount-ro,usrquota,grpquota 0       1
/dev/sda5       none            swap    sw              0       0
/dev/hdd        /media/cdrom0   udf,iso9660 user,noauto     0       0



```


however my mtab shows that missing hard drive i want shown, on the very last line:

```

/dev/sda1 / ext3 rw,errors=remount-ro,usrquota,grpquota 0 0
proc /proc proc rw 0 0
/sys /sys sysfs rw 0 0
varrun /var/run tmpfs rw 0 0
varlock /var/lock tmpfs rw 0 0
procbususb /proc/bus/usb usbfs rw 0 0
udev /dev tmpfs rw 0 0
devpts /dev/pts devpts rw,gid=5,mode=620 0 0
devshm /dev/shm tmpfs rw 0 0
lrm /lib/modules/2.6.15-27-386/volatile tmpfs rw 0 0
/dev/hdd1 /home/clinton/hdd1 reiserfs rw 0 0

```

How would i remount my hard drive, "/dev/hdd1", again so it no longer has a segmentation fault in CLI?

You could always run sudo mount /dev/hdd1 [location] to mount your disk.

Something else concerns me, though. According to your /etc/fstab, hdd is a cdrom drive, but your /etc/mtab shows it as a partitioned hard disk. Something is getting confused along the way, probably at bootup. My best guess is that df is looking for the information in that particular drive, expecting it to be in one format. When it doesn't find what it's looking for, it throws up its hands, screams, and segfaults.

My best guess is that getting the hdd settings correct will fix things. Maybe try replacing the last line in /etc/fstab with:

```

/dev/hdd1        [mountpoint]   reiserfs     0       0

```

appropriately substituting the mountpoint.

---

### Post by afbase on 2007-07-03
this is what my fstab looks like now, i commented out my cd - drive, I don't really use anyways so isn't necessary for it to be mounted.

> # /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/sda1       /               ext3    defaults,errors=remount-ro,usrquota,grpquota 0       1
/dev/sda5       none            swap    sw              0       0
#/dev/hdd        /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/hdd1       /home/clinton/hdd1      reiserfs  0 0


Well to give you more hints to my problem, I'll show you what else  i've done so far
```
 
mount /dev/hdd1 /home/clinton/hdd1
df



```
df only returns "Segmentation fault".  I also noticed my Mysql db is not working either

```

/etc/init.d/mysql restart

```
this returns 
> 
Stopping MySQL database server: mysqld.
/etc/init.d/mysql[6350]: ERROR: The partition with /var/lib/mysql is too full!


/var/lib/mysql is located on /dev/sda1.  Could the problem be sda1?

---

### Post by afbase on 2007-07-03
please help!!!

---

### Post by pbaumgar on 2007-07-03
Do you get seg faults with any other commands?  Might be that you've got some hard drive problems.  Type 'dmesg' on the command line to show the kernel messages and see if there are any errors there...

---

### Post by pjkoczan on 2007-07-03
> **afbase said:**
> this is what my fstab looks like now, i commented out my cd - drive, I don't really use anyways so isn't necessary for it to be mounted.


Well, I could be wrong, but I think it should be mounted so the OS can autodetect when you put a cd in. The problem isn't likely that you have a CD drive, it's that you used the wrong name to refer to it. It's probably /dev/hd_ (a, b, or c), if your harddrive truly is /dev/hdd. Fix the naming, and you'll be good in the future.

> 
Well to give you more hints to my problem, I'll show you what else  i've done so far
```
 
mount /dev/hdd1 /home/clinton/hdd1
df


```
df only returns "Segmentation fault".  


Did you unmount the cd drive (umount /media/cdrom0 should do the trick) or reboot? df is probably still looking for data where it shouldn't. Unmounting the cd drive or rebooting with a good fstab should cause df to stop looking where it shouldn't.

> 
I also noticed my Mysql db is not working either

```

/etc/init.d/mysql restart

```
this returns 


/var/lib/mysql is located on /dev/sda1.  Could the problem be sda1?

It's unlikely your seg fault is related to this, but I would probably recommend cleaning up your drive or moving your mysql data to a less full disk.

> 
please help!!!


Relax. It's been less than an hour, someone will see your problem.

---

### Post by afbase on 2007-07-04
Is this segmenation fault an partitioning error

i tried 
```
 fsck -A
```
> WARNING!!!  Running e2fsck on a mounted filesystem may cause
SEVERE filesystem damage.

Do you really want to continue (y/n)? yes

/dev/sda1: recovering journal
/dev/sda1: clean, 116174/2142112 files, 1024827/4279306 blocks


then
```
df
```

I still get segmentation fault. I'm suspecting that my /dev/sda1 is the problem.  My Mysql data/server is based on that hard drive, and it is no longer functioning properly.   


Does anybody have a possible solution?????

---

### Post by afbase on 2007-07-04
i tried "fsck -pc /dev/sda1"

i rebooted and still segmentation fault.


PLEASE HELP!!!!!

---

### Post by PaulFr on 2007-07-04
1. Can you post any error messages you see in the output of **dmesg** ?
2. Can you run **sudo fdisk -l /dev/hdd** and **sudo fdisk -l /dev/sda** and post the output.
3. Can you run **df** as **strace df** and post the last 20-30 lines of the trace ? It will show you the system calls being made by df.

---

