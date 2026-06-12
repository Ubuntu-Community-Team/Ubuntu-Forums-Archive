---
title: "Problems with tmpfs"
date: 2013-01-20
forum: General Help
---

### Post by Pershin on 2013-01-20
Hello community! I have a little problem and I can not solve it.
I want to move /.cache and /tmp folders into RAM. 
I tried to do it:
```

$ cat /etc/fstab
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda1 during installation
UUID=7472aeb5-7765-4d45-b43c-93f2f56a66d4 /               ext4    errors=remount-ro 0       1
# /home was on /dev/sda3 during installation
UUID=a25d76a5-9498-4204-9e2c-d46bb2bbc514 /home           ext4    defaults        0       2
# /media/Media was on /dev/sda5 during installation
UUID=0FF6427871962D57 /media/Media    ntfs    defaults,umask=007,gid=46 0       0
# swap was on /dev/sda2 during installation
#UUID=86efbe37-8c79-435b-8272-405cd938a2a0 none            swap    sw              0       0
/dev/mapper/cryptswap1 none swap sw 0 0
[U]tmpfs /tmp tmpfs defaults 0 0
tmpfs /home/pershin/.cache tmpfs defaults 0 0[/U]

```
But I do not see any profit. After rebooting the /.cache is still 400+ MB. Its content has not changed. I created test file in both folders. After a new reboot in the /tmp it had disappeared (I think it always happens in a /tmp, even without tmpfs), and in the /.cache it remained. 
But this could not be, if folders are in the RAM. 
What did I do wrong?
```

$ mount
/dev/sda1 on / type ext4 (rw,errors=remount-ro)
proc on /proc type proc (rw,noexec,nosuid,nodev)
sysfs on /sys type sysfs (rw,noexec,nosuid,nodev)
none on /sys/fs/fuse/connections type fusectl (rw)
none on /sys/kernel/debug type debugfs (rw)
none on /sys/kernel/security type securityfs (rw)
udev on /dev type devtmpfs (rw,mode=0755)
devpts on /dev/pts type devpts (rw,noexec,nosuid,gid=5,mode=0620)
tmpfs on /tmp type tmpfs (rw)
tmpfs on /run type tmpfs (rw,noexec,nosuid,size=10%,mode=0755)
none on /run/lock type tmpfs (rw,noexec,nosuid,nodev,size=5242880)
none on /run/shm type tmpfs (rw,nosuid,nodev)
/dev/sda5 on /media/Media type fuseblk (rw,nosuid,nodev,allow_other,default_permissions,blksize=4096)
/dev/sda3 on /home type ext4 (rw)
tmpfs on /home/pershin/.cache type tmpfs (rw)
/home/pershin/.Private on /home/pershin type ecryptfs (ecryptfs_check_dev_ruid,ecryptfs_cipher=aes,ecryptfs_key_bytes=16,ecryptfs_unlink_sigs,ecryptfs_sig=aed8a71a771e010c,ecryptfs_fnek_sig=ad78c26fd4552988)
gvfs-fuse-daemon on /home/pershin/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=pershin)

```
```

$ df -h 
/dev/sda1                 15G         8,7G  5,1G           64% /
udev                     1,9G         4,0K  1,9G            1% /dev
tmpfs                    2,0G          64K  2,0G            1% /tmp
tmpfs                    791M         904K  790M            1% /run
none                     5,0M         8,0K  5,0M            1% /run/lock
none                     2,0G         636K  2,0G            1% /run/shm
/dev/sda5                403G         373G   30G           93% /media/Media
/dev/sda3                 44G          12G   32G           28% /home
tmpfs                     44G          12G   32G           28% /home/pershin/.cache
/home/pershin/.Private    44G          12G   32G           28% /home/pershin

```
tmpfs = 44G = size of /home. I have only 4G RAM. What is this?
```

grep cache /proc/mounts
tmpfs /home/pershin/.cache tmpfs rw,relatime 0 0

```
```

$ findmnt -kR /home
TARGET                  SOURCE                 FSTYPE            OPTIONS
/home                   /dev/sda3              ext4              rw,relatime,user_xattr,barrier=1,data=ordered
&#9500;&#9472;/home/pershin/.cache  tmpfs                  tmpfs             rw,relatime
&#9492;&#9472;/home/pershin         /home/pershin/.Private ecryptfs          rw,relatime,ecryptfs_fnek_sig=ad78c26fd4552988,ecryptfs_sig=aed8a71a771e010c,ecryptfs_cipher=aes,ecryptfs
  &#9492;&#9472;/home/pershin/.gvfs gvfs-fuse-daemon       fuse.gvfs-fuse-da rw,nosuid,nodev,relatime,user_id=1000,group_id=1000

```

I hope very much for your help!

---

### Post by tgalati4 on 2013-01-20
What exactly are you trying to accomplish?  I think you have set up a circular reference since the user has access to /tmp as well as the system (via tmpfs), both now pointing to a RAMdisk.  I think bad things would happen under certain situations.  Does the system feel much faster with these RAMdisks?

I don't know how tmpfs works, but it's possible that you really have two .cache directories.  Your original ~/.cache directory and the one created in tmpfs and you can read and write files into both directories.  Just like a linked directory, you have a local directory as the mount point (link name) and the Target (the actual final destination) and you can have files in both, but only read one at a time.

---

### Post by Pershin on 2013-01-22
The problem was that the /home/pershin/.cache folder was mounted (in /etc/fstab) before /home/pershin folder (/etc/pam.d). The libpam-mount package (pam_mount) has helped me.

---

