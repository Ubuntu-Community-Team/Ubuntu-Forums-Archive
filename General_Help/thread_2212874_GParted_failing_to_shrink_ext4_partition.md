---
title: "GParted failing to shrink ext4 partition"
date: 2014-03-23
forum: General Help
---

### Post by alex172 on 2014-03-23
I installed Linux recently wiping all the data I had previously. I want to install windows alongside Ubuntu, and I'm trying to create an NTFS partition.

At the moment Ubuntu is installed on 700Gb ext4 partition, I am trying to shrink it to 100Gb.
I am booting from LiveUSB when I am trying to shrink the partition.
I'm including the GParted logfile, and I have tried the solution at the end with no success.

Thanks

---

### Post by slooksterpsv on 2014-03-23
Are you booted into that system or off of a LiveCD?

---

### Post by alex172 on 2014-03-23
I'm not on the system, I'm booted through LiveUSB (same as LiveCD)

---

### Post by oldfred on 2014-03-23
It is showing some error. I would try running fsck from your live installer. 
How full is your ext4 partition?

       #From liveCD so everything is unmounted,swap off if necessary, change example shown with partition sdb1 to your partition(s)
#e2fsck is used to check the ext2/ext3/ext4 family of file systems. -p trys fixes where response not required
sudo e2fsck -C0 -p -f -v /dev/sdb1
#if errors: -y auto answers yes for fixes needing response, also see man e2fsck
sudo e2fsck -f -y -v /dev/sdb1

---

### Post by alex172 on 2014-03-23
My partition had 15GB of data. It was a fresh install so I didn't have any important data, I used brute force and formated the drive, partitioning it properly during the install. Not elegant but it took less time.
I guess we won't know what works.
THanks for the help anyway :)

---

