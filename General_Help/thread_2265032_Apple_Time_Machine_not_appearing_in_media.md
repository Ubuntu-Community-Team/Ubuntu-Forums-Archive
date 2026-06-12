---
title: "Apple Time Machine not appearing in /media"
date: 2015-02-12
forum: General Help
---

### Post by earthpigg on 2015-02-12
Hello,

Former linux nerd, but skills have atrophied as I stopped using them.

Apple Time Machine Volume on an external hard drive. No Mac available. I am certain the external hard drive itself is fine b/c my buddy installed some shareware crap on a Windows computer, which allows partial/limited/stupid access to it when plugged into that machine.

I can google all the guides to see how to access it, but they all presume it appears in /media. I see nothing there.

Have installed hfsutils, hfsprogs, and so on.

I unplugged the thing and hit mount, and then plugged it in to find the new thing appearing, but no new thing appeared. 

```

[chris: /media]$ ls -a
.  ..
[chris: /media]$ mount
/dev/sdb1 on / type ext4 (rw,errors=remount-ro)
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
/dev/sda1 on /home type ext4 (rw)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw,noexec,nosuid,nodev)
/home/chris/.Private on /home/chris type ecryptfs (ecryptfs_check_dev_ruid,ecryptfs_cipher=aes,ecryptfs_key_bytes=16,ecryptfs_unlink_sigs,ecryptfs_sig=2fec71a5c7ee1f6c,ecryptfs_fnek_sig=fefdbf20ee4ce598)
gvfs-fuse-daemon on /home/chris/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=chris)
[chris: /media]$ PLUGGING IT IN NOW
PLUGGING: command not found
[chris: /media]$ mount
/dev/sdb1 on / type ext4 (rw,errors=remount-ro)
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
/dev/sda1 on /home type ext4 (rw)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw,noexec,nosuid,nodev)
/home/chris/.Private on /home/chris type ecryptfs (ecryptfs_check_dev_ruid,ecryptfs_cipher=aes,ecryptfs_key_bytes=16,ecryptfs_unlink_sigs,ecryptfs_sig=2fec71a5c7ee1f6c,ecryptfs_fnek_sig=fefdbf20ee4ce598)
gvfs-fuse-daemon on /home/chris/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=chris)
[chris: /media]$ ^C
[chris: /media]$ ls -a
.  ..


```

Am using whatever version of Ubuntu has kernel 3.2.0-24-generic.

Any help would be appreciated, thanks!

---

### Post by bapoumba on 2015-02-12
This is not going to help you much, I had never though about plugging one of my Mac external drives onto my Ubuntu laptop :)
The drive does mount in /media :
```
/dev/sdb2 on /media/bapoumba/Backups_MBP type hfsplus (ro,nodev,nosuid,uhelper=udisks2)
/dev/sdb3 on /media/bapoumba/Storage type hfsplus (ro,nodev,nosuid,uhelper=udisks2)

```
Ubuntu 14.10 here with 3.16.0-30-generic. Looks like you are on 12.04 ?
I have not installed anything particular, at least not intentionally, and the drive mounted right away.

As I have now tried, the drive is indeed read only (from what i've read, you have to turn off journaling from OSX to be able to write). But it does mount fine and I can browse both my files and the Time Machine backup.

---

