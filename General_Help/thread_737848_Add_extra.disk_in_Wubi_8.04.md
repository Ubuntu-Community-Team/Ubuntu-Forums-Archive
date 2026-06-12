---
title: "Add extra.disk in Wubi 8.04"
date: 2008-03-28
forum: General Help
---

### Post by zorblek on 2008-03-28
I'm trying to increase the amount of space I have to work with in Wubi 8.04 on Windows XP. I tried renaming a large file extra.disk and moving it into C:\ubuntu\disks like it suggests on the project page. However, after restarting I didn't have any more space available. Is there something more that I need to do? I did this with a different wubi install (7.04), and had no problems.

---

### Post by ago on 2008-03-28
> **zorblek said:**
> I'm trying to increase the amount of space I have to work with in Wubi 8.04 on Windows XP. I tried renaming a large file extra.disk and moving it into C:\ubuntu\disks like it suggests on the project page. However, after restarting I didn't have any more space available. Is there something more that I need to do? I did this with a different wubi install (7.04), and had no problems.

The extra.disk is not directly supported in 8.04... You will have to do it manually.

sudo mkfs.ext3 /ubuntu/disks/extra.disk
sudo mkdir /media/extra
sudo mount -o loop /ubuntu/disks/extra.disk /media/extra

Now /media/extra should be available, you have 2 options

1) copy over /usr or /home.
You will then have to add the mountpoint in /etc/fstab

2) copy over all of /
You will have to skip /proc/* /tmp/* and /sys/*
Then you have to rename extra.disk -> root.disk

---

