---
title: "&quot;unable to mount&quot; warnings at boot time"
date: 2013-09-03
forum: General Help
---

### Post by George Heine on 2013-09-03
Hello - installed 12.04.1 about a year ago.  
```
cat /proc/version
Linux version 3.2.0-52-generic-pae (buildd@batsu) (gcc version 4.6.3 (Ubuntu/Linaro 4.6.3-1ubuntu5) ) #78-Ubuntu SMP Fri Jul 26 16:43:19 UTC 2013
```
Several weeks ago, system started giving me the following message at boot time:
```
The disk drive for /tmp is not ready yet or not present.
Press S to skip mounting, or M to ...., or continue to wait.
```

(Sorry, had to capture this message by hand, didn't have time to write all the details).  After a short wait, the system goes ahead and boots and runs normally.

Here are the relevant parts of /etc/fstab

```
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda1 during installation
UUID=1f8881c6-6a58-4761-b63e-fc4c662618bd /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda5 during installation
UUID=94009d41-f2d8-445a-8678-073d7c8d4fd3 none            swap    sw              0       0
#/tmp/loop.iso   /media/loop        iso9660 noauto,user,ro,loop=/dev/loop0 0 0
```

The last line does have an instruction to mount something from /tmp, but is commented out and is specified as "noauto".

Or is there somewhere else that I need to look?

The /tmp/loop.iso line in fstab was meant to be a convenient way of looking at disk images before burning to media.
It did allow mounting with the command
```
mount /media/loop
```
but system gave an error when trying to umount:  
```
umount: /media/loop mount disagrees with the fstab
```
Needed to go into sudo to umount.

This is only a minor inconvenience, but any insights would be welcome.

---

### Post by maestrobwh1 on 2013-09-03
This used to happen in older ubuntus:  /etc/mtab would leave a record of a "zombie" mount.

Just a hunch, but check /etc/mtab and see if there is a reference to the iso file?

---

### Post by George Heine on 2013-09-04
> Just a hunch, but check /etc/mtab and see if there is a reference to the iso file?                             21 Hours Ago
         

Here it is.  I don't see anything in here, but maybe another pair of eyes will spot something.
What happens if /etc/mtab is deleted?

```
$ cat /etc/mtab
/dev/sda1 / ext4 rw,errors=remount-ro 0 0
proc /proc proc rw,noexec,nosuid,nodev 0 0
sysfs /sys sysfs rw,noexec,nosuid,nodev 0 0
none /sys/fs/fuse/connections fusectl rw 0 0
none /sys/kernel/debug debugfs rw 0 0
none /sys/kernel/security securityfs rw 0 0
udev /dev devtmpfs rw,mode=0755 0 0
devpts /dev/pts devpts rw,noexec,nosuid,gid=5,mode=0620 0 0
tmpfs /run tmpfs rw,noexec,nosuid,size=10%,mode=0755 0 0
none /run/lock tmpfs rw,noexec,nosuid,nodev,size=5242880 0 0
none /run/shm tmpfs rw,nosuid,nodev 0 0
gvfs-fuse-daemon /home/XX/.gvfs fuse.gvfs-fuse-daemon rw,nosuid,nodev,user=XX 0 0

```

---

### Post by VMC on 2013-09-04
Here's a current [bug report]("https://bugs.launchpad.net/ubuntu/+source/mountall/+bug/1091792") on this.

Here's my "/etc/init/mountall.conf":

```
# mountall - Mount filesystems on boot#
# This helper mounts filesystems in the correct order as the devices
# and mountpoints become available.


description	"Mount filesystems on boot"


start on startup
stop on starting rcS


expect daemon
task


emits virtual-filesystems
emits local-filesystems
emits remote-filesystems
emits all-swaps
emits filesystem
emits mounting
emits mounted


# temporary, until we have progress indication
# and output capture (next week :p)
console output


script
    . /etc/default/rcS
    [ -f /forcefsck ] && force_fsck="--force-fsck"
    [ "$FSCKFIX" = "yes" ] && fsck_fix="--fsck-fix"


    # set $LANG so that messages appearing in plymouth are translated
    if [ -r /etc/default/locale ]; then
        . /etc/default/locale
        export LANG LANGUAGE LC_MESSAGES LC_ALL
    fi


    exec mountall --daemon $force_fsck $fsck_fix
end script


post-stop script
    rm -f /forcefsck 2>dev/null || true
end script
```Is yours like this?

---

### Post by George Heine on 2013-09-05
> Here's my "/etc/init/mountall.conf":
...
Is yours like this?


Yes, it's identical (except for a few blank lines)

---

