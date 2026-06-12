---
title: "Are these proper &quot;relatime mount options&quot;, for my File Systems?"
date: 2012-10-28
forum: General Help
---

### Post by mikodo on 2012-10-28
Hi,

I am trying to check the relatime mount options on my File Systems. As I understand it, the relatime mount option saves on disk writing, hence increases the longevity of them.

Here are mine. Are they OK?

```
cat /proc/mounts

```rootfs / rootfs rw 0 0
none /sys sysfs rw,nosuid,nodev,noexec,relatime 0 0
none /proc proc rw,nosuid,nodev,noexec,relatime 0 0
none /dev devtmpfs rw,relatime,size=2051852k,nr_inodes=207572,mode=755 0 0
none /dev/pts devpts rw,nosuid,noexec,relatime,gid=5,mode=620,ptmxmode=000 0 0
/dev/disk/by-uuid/1b3bf77f-702f-45fc-831b-404daba90305 / ext4 rw,relatime,barrier=1,data=ordered 0 0
none /sys/fs/fuse/connections fusectl rw,relatime 0 0
none /sys/kernel/debug debugfs rw,relatime 0 0
none /sys/kernel/security securityfs rw,relatime 0 0
none /dev/shm tmpfs rw,nosuid,nodev,relatime 0 0
none /var/run tmpfs rw,nosuid,relatime,mode=755 0 0
none /var/lock tmpfs rw,nosuid,nodev,noexec,relatime 0 0
none /lib/init/rw tmpfs rw,nosuid,relatime,mode=755 0 0
/dev/sda5 /home ext4 rw,relatime,barrier=1,data=ordered 0 0
/dev/sda7 /media/VBox ext4 rw,relatime,barrier=1,data=ordered 0 0
binfmt_misc /proc/sys/fs/binfmt_misc binfmt_misc rw,nosuid,nodev,noexec,relatime 0 0
gvfs-fuse-daemon /home/mikodo/.gvfs fuse.gvfs-fuse-daemon rw,nosuid,nodev,relatime,user_id=1000,group_id=1000 0 0
/dev/sdf1 /media/0f7f47da-4739-403b-88b6-6a4ee18e1c22 ext4 rw,nosuid,nodev,relatime,barrier=1,data=ordered 0 0
/dev/sdf3 /media/1b111bab-99cf-42cd-939d-daad8f0de282 ext4 rw,nosuid,nodev,relatime,barrier=1,data=ordered 0 0
/dev/sdf2 /media/005db7cd-6b76-4f88-be85-25d1a8573578 ext4 rw,nosuid,nodev,relatime,barrier=1,data=ordered 0 0
mikodo@mikodo-desktop:~$

Thanks.

---

### Post by hal8000 on 2012-10-28
The relatime option only updates access time  if the previous access time was earlier than the current modify or change time. It can improve disk performance.

However if you want to tune your ext4 for faster access (without updating inode access times, modify your /etc/fstab with noatime, nodirtime options.

Example

/dev/sda1  /        ext4   defaults,noatime,nodirtime,relatime  0 1
/dev/sda2  /home    ext4   defaults,noatime,nodirtime,relatime   0 2
etc

repalce sda1 and sda2 with your correct partitions.
More help can be found below:

[https://wiki.archlinux.org/index.php/Fstab](https://wiki.archlinux.org/index.php/Fstab)


 or the manpage of fstab, from a terminal with:

man fstab

---

### Post by mikodo on 2012-10-28
Thanks, hal8000.

I'll look into these.

---

