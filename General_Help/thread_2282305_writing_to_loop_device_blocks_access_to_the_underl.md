---
title: "writing to loop device blocks access to the underlying filesystem"
date: 2015-06-13
forum: General Help
---

### Post by lvm on 2015-06-13
FAT32 disk image is stored as a file on an ext4 filesystem and is mounted as a loop device. When large amount of data is being written to the loop device access to the underlying ext4 filesystem starts periodically freezing for a few seconds: 100% wio and nothing's happening; process writing to the loop device freezes too. Any ideas on what's the cause and how to fix it? My hypothesis is that loop device is periodically synced and it somehow causes the whole underlying filesystem to be synced instead of just the image file.

---

