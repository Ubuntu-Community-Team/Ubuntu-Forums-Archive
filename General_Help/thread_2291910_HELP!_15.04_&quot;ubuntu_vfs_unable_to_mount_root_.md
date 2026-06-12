---
title: "HELP! 15.04: &quot;ubuntu vfs unable to mount root fs on unknown-block(0, 0)&quot;"
date: 2015-08-23
forum: General Help
---

### Post by varun10 on 2015-08-23
Here is an image of what I see: [https://i.imgur.com/oBOPOcC.jpg](https://i.imgur.com/oBOPOcC.jpg)

---

### Post by varun10 on 2015-08-23
[COLOR=#000000]Here is an image of what I see: [/COLOR][https://i.imgur.com/oBOPOcC.jpg](https://i.imgur.com/oBOPOcC.jpg)

---

### Post by Petro Dawg on 2015-08-23
Might help to know what you were doing before this occurred.  Is this a new install, or did you try to re-partition something after the installation?  Is this a dual boot?

---

### Post by varun10 on 2015-08-23
> **Petro Dawg said:**
> Might help to know what you were doing before this occurred.  Is this a new install, or did you try to re-partition something after the installation?  Is this a dual boot?


I reinstalled ubuntu and I split my HDD (500 gb) into two partitions during the installation. It's not a dual boot anymore since I formatted the entire hdd before installing ubuntu again

---

### Post by varun10 on 2015-08-24
Bump

---

### Post by varun10 on 2015-08-24
Bump

---

### Post by oldfred on 2015-08-24
Duplicate threads merged. Please only one thread per topic.
We all are volunteers and do not need to waste effort on answer if already answered in another thread.

You may need to run fsck on partitions if both are ext4?

 #From liveDVD/Flash so everything is unmounted,swap off if necessary, change example shown with partition sdb1 to your partition(s)
#e2fsck is used to check the ext2/ext3/ext4 family of file systems. -p trys fixes where response not required
sudo e2fsck -C0 -p -f -v /dev/sdb1
#if errors: -y auto answers yes for fixes needing response, also see man e2fsck
sudo e2fsck -f -y -v /dev/sdb1

---

