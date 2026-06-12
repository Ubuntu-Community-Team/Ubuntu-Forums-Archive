---
title: "Running Fsck"
date: 2019-11-11
forum: General Help
---

### Post by sniper8752 on 2019-11-11
I have a dell laptop, and it has nvme on it.  There is no /dev/sd*, only nvme0.  I tried running fsck against this device, but it said this: "fsck.ext2: Illegal seek while trying to open /dev/nvme0".  Please advise.

---

### Post by oldfred on 2019-11-11
You can only run fsck on the ext family of formats and only on one partition at a time, not on a drive.
Note that NVMe devices are named by /dev/nvme[device number]n[namespace number]p[partition number].
This means if you format your NVMe device with at least one partition, you'll end up with at least three devices: /dev/nvme0, /dev/nvme0n1 and /dev/nvme0n1p1

To see all the ext4 partitions
sudo parted -l
#From liveDVD/Flash so everything is unmounted,swap off if necessary, change example shown with partition sdb1 to your partition(s)
#e2fsck is used to check the ext2/ext3/ext4 family of file systems. -p tries fixes where response not required
sudo e2fsck -C0 -p -f -v /dev/sdb1
# -y auto answers yes for fixes needing response, also see man e2fsck
sudo e2fsck -f -y -v /dev/sdb1

And then in your case you replace /dev/sdb1 with /dev/nvme0n1p1 or whatever parted shows are ext4 partition(s).

---

### Post by TheFu on 2019-11-11
```
$ lsblk -o name,size,type,fstype,mountpoint
```
Will show the file system type as well as a nice summary of other important storage info.

---

