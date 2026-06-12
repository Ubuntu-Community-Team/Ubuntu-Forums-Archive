---
title: "Fstab fails to mount - 12.10"
date: 2012-11-25
forum: General Help
---

### Post by synnedue on 2012-11-25
I cannot get fstab to mount my /home partition which resides on a secondary disk.  I just upgraded my system where I have had no issues previously.

I can manually mount the partition without errors. I have no idea what to do - not sure if this is a bug or not?

```
$ sudo blkid
/dev/sda1: UUID="200203f1-393d-498e-96c0-e00d790a3de3" TYPE="ext4" 
/dev/sda5: UUID="a70ce3ae-bb4f-4722-b661-b40c5451f0d7" TYPE="swap" 
/dev/sdb1: UUID="cf1fa66c-1d75-4d41-8f4e-3e9864f21e61" TYPE="xfs"
```

/etc/fstab (with comments)
```

# /etc/fstab: static file system information.
#
# Use 'blkid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda1 during installation
UUID=200203f1-393d-498e-96c0-e00d790a3de3 /               ext4    errors=remount-ro 0       1

# mount order? try to mount /dev/sdb1 as /home before swap -- no joy
#/dev/sdb1 /home xfs nodev,nosuid 0 2

# swap was on /dev/sda5 during installation
UUID=a70ce3ae-bb4f-4722-b661-b40c5451f0d7 none            swap    sw              0       0
# mount /dev/sdb1 as /home
# try using UUID or /dev/sdb1 -- no joy
UUID=cf1fa66c-1d75-4d41-8f4e-3e9864f21e61 /home           xfs     nodev,nosuid    0       2
#/dev/sdb1 /home xfs nodev,nosuid 0 2

```

On boot:

```
Serious errors were found wile checking the disk drive for /home.
Press I to ignore, S to skip mounting, or M for manual recovery

[M]

# mount
/dev/sda1 on / type ext4 (rw,errors=remount-ro)
proc on /proc type proc (rw,noexec,nosuid,nodev)
sysfs on /sys type sysfs (rw,noexec,nosuid,nodev)
none on /sys/fs/fuse/connections type fusectl (rw)
none on /sys/kernel/debug type debugfs (rw)
none on /sys/kernel/security type securityfs (rw)
udev on /dev type devtmpfs (rw,mode=0755)
devpts on /dev/pts type devpts (rw,noexec,nosuid,gid=5,mode=0620)
tmpfs on /run type tmpfs (rw,noexec,nosuid,size=10%,mode=0755)
none on /run/lock type tmpfs (rw,noexec,nosuid,nodev,size=5242880)
none on /run/shm type tmpfs (rw,nosuid,nodev)
none on /run/user type tmpfs (rw,noexec,nosuid,nodev,size=104857600,mode=0755)

# ls -l /home

# mount -a

# ls -l /home
drwxr-xr-x 29 monica monica 4096 Nov 25 13:53 monica

[Ctrl-D]

system continues normally to login window
```

This was not a problem before my upgrade, and isnt a problem after manually mounting /home from recovery -- fstab just doesnt want to behave.  Anyone have any suggestions, please?

Thanks

---

### Post by synnedue on 2012-11-25
I am still having no joy resolving this problem.  I have tried different mount options in fstab and still nothing mounts my partition.... but no error exists when manually mounting.

For now my system runs smoothly until a roboot where /home is not mounted again.

Looking for any suggestions.  Thanks

---

### Post by oldfred on 2012-11-26
> Serious errors were found wile checking the disk drive for /home.
Press I to ignore, S to skip mounting, or M for manual recovery


If you had ext4 I would suggest fsck, but know nothing about xfs. Is there an equivalent command for the xfs system as it looks like it needs repairs.

---

### Post by rnerwein on 2012-11-26
> **oldfred said:**
> If you had ext4 I would suggest fsck, but know nothing about xfs. Is there an equivalent command for the xfs system as it looks like it needs repairs.
i see you ain't have the blkid for /home in your fstab. i got the ( i think so) same jokes on my box too. i have three disks (one internal - ubuntu, second usb - suse and a third esa - solaris. and the suse and solaris disks change from /dev/sdb1, /dev/sdfx or /dev/sdh.
why ? thats life for dynamic. try the blkid.

---

### Post by synnedue on 2012-11-26
oldfred: I believe the serious error is that /home is empty (?) because the mount never happens... I have a spare drive I might spin as ext4 and see if the problems persists as well as an xfs repair. Thanks for the suggestions. 

rnerwein: Infact, I am using the UUID. Last uncommented line in fstab.

Everything Ive read from documentation is correct in my fstab and should work without issue as it did in 10.04 just before upgrading this system.  Again, my system is working flawlessly as I type this reply: Only, that I have to mount /home manually. I just dont get it.

---

### Post by LewisTM on 2012-11-26
Do you have package xfsprogs installed?
I had this happen to me once. Problem is that you partition is set to undergo a filesystem check after a set number of mounts or after some time. Without xfsprogs, there is no fsck.xfs and the filesystem fails to mount. Disabling fsck with a 0 instead of a 2 at the end of your fstab entry would also let you boot without automatic fs check.

Cheers!

---

### Post by rnerwein on 2012-11-26
> **LewisTM said:**
> Do you have package xfsprogs installed?
I had this happen to me once. Problem is that you partition is set to undergo a filesystem check after a set number of mounts or after some time. Without xfsprogs, there is no fsck.xfs and the filesystem fails to mount. Disabling fsck with a 0 instead of a 2 at the end of your fstab entry would also let you boot without automatic fs check.

Cheers!
try: lsmod | grep xfs --> i think it's not loaded.
insert in /etc/modules:

#  by richi
ufs
xfs

works after reboot. or you can directly load it with: modprobe

---

### Post by synnedue on 2012-11-26
lewisTM: xfsprogs was not installed. Installing now and crossing figers.

rnerwein: xfs does appear to be loaded. I assume your later additions to /etc/modules is not needed due to this?

```
$ lsmod | grep xfs
xfs                   744277  1 
```

---

### Post by synnedue on 2012-11-26
lewisTM: Spot on, thanks so much :) I've just rebooted without errors.

Marking as solved: Installation of xfsprogs resolved my earlier reported issues.

Thanks all for your time and attention to this, I am greatly appreciative you took the time to read and comment.  God bless!

---

### Post by LewisTM on 2012-11-26
Did you do a clean install when upgrading? I'd bet you did.

That should be a warning to other xfs users. The installer is too dumb to detect that there is an xfs partition present and that a helper package is needed. Fortunately, xfs support (i.e. mounting an xfs volume and read/writing) is part of the official kernel. To repair one, xfsprogs is needed.

Oh, and please mark the thread as SOLVED.

---

