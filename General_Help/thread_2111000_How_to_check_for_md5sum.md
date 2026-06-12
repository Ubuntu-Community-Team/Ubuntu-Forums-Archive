---
title: "How to check for md5sum"
date: 2013-01-31
forum: General Help
---

### Post by Juniorr on 2013-01-31
So I have a md5sum in my DVD, and I'd like to check it's contents integrity. Where do I verify that? Ubuntu mdums only shows the whole DVD's sum, not each archive's one.

Thanks in advance.

---

### Post by papibe on 2013-01-31
Hi Juniorr.

Make sure the DVD is mounted, for instance on /cdrom. Then run md5sum with the option -c. That tells md5sum to both calculate the checksums and compare them with the content of the file:
```
cd /cdrom

md5sum -c md5sum.txt
```
Hope it helps. Let us know how it goes.
Regards.

---

### Post by Juniorr on 2013-01-31
md5sum: md5sum.txt: No such file or directory

Just noticed it's not mounted on /cdrom. How do I mount it?

---

### Post by papibe on 2013-01-31
Is it mounted?

Could you post the result of this commands?
```
df -h

mount -l

ls /cdrom
```
Regards.

---

### Post by Juniorr on 2013-01-31
df -h
```
df: `/root/.gvfs': Permission denied
Filesystem      Size  Used Avail Use% Mounted on
/dev/sda1       276G  3.3G  258G   2% /
udev            1.9G  4.0K  1.9G   1% /dev
tmpfs           791M  780K  791M   1% /run
none            5.0M     0  5.0M   0% /run/lock
none            2.0G  224K  2.0G   1% /run/shm
/dev/sr0        695M  695M     0 100% /media/Ubuntu 12.04.1 LTS amd64
```_______________________________________________
mount -l
```
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
gvfs-fuse-daemon on /home/a/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=a)
gvfs-fuse-daemon on /root/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev)
/dev/sr0 on /media/Ubuntu 12.04.1 LTS amd64 type iso9660 (ro,nosuid,nodev,uid=1000,gid=1000,iocharset=utf8,mode=0400,dmode=0500,uhelper=udisks) [Ubuntu 12.04.1 LTS amd64]
```____________________________________________________

ls /cdrom

No output

---

### Post by papibe on 2013-01-31
It is not mounted on /cdrom but '/media/Ubuntu 12.04.1 LTS amd64'

Try again:
```
cd '/media/Ubuntu 12.04.1 LTS amd64'

md5sum -c md5sum.txt
```
Let us know how it goes.
Regards.

---

### Post by Juniorr on 2013-01-31
Thank you! I noticed it was mounted on /media, but I thought it was required to be mounted on /cdrom. Anyway, it verifies the mdsums on the CD with the ones online, right?

---

### Post by Juniorr on 2013-01-31
Just one more thing?

If some of these files were altered, this could mean a malicious code?
If everything is OK, then it's safe to install the system?

---

### Post by papibe on 2013-01-31
> **Juniorr said:**
> it verifies the mdsums on the CD with the ones online, right?
Not exactly.

The file 'md5sum.txt' is included on the root of the CD/DVD image, so you can check the files manually.

Regards.

---

### Post by papibe on 2013-01-31
> **Juniorr said:**
> If some of these files were altered, this could mean a malicious code?
It may, but most of the time it would a reflect corrupt download.

It is important to download the image only from the Ubuntu website ([http://www.ubuntu.com/]("http://www.ubuntu.com/")). That would be the safest way to get it.

> **Juniorr said:**
> If everything is OK, then it's safe to install the system?
If you downloaded the ISO from the Ubuntu website, and the checksum is OK, it is safe to start the installation process.

Does that answer your concerns?
Regards.

---

### Post by Juniorr on 2013-02-01
Yes, all my concerns were answered, thanks!

---

### Post by varunendra on 2013-02-01
> **Juniorr said:**
> Yes, all my concerns were answered, thanks!

Then please mark the thread as [Solved] using "Thread Tools" link above your post.

PS:
To add to whatever papibe suggested, I'd recommend to download the ISO via torrent. Hash checking is an inherent property of torrent (p2p) protocol, thus ensuring integrity of downloaded data (more reliable than md5sum); and is usually faster than a direct download.

Official links for torrent downloads : [http://www.ubuntu.com/download/desktop/alternative-downloads](http://www.ubuntu.com/download/desktop/alternative-downloads)

---

