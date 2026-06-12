---
title: "preseed choose between /dev/sda and mmcblk0 for unattended install"
date: 2015-08-20
forum: General Help
---

### Post by roland-logikalsolutions on 2015-08-20
Hit a real snag others must have hit as well. This snippet works fine in unattended install for both VM and desktop:

d-i partman-auto/disk string /dev/sda
d-i partman-auto/method string regular
d-i partman-lvm/device_remove_lvm boolean true
d-i partman-md/device_remove_md boolean true
d-i partman-lvm/confirm boolean true
d-i partman/choose_partition select finish
d-i partman-auto/guided_size string max
# - atomic: all files in one partition
d-i partman-auto/choose_recipe select atomic
d-i partman/default_filesystem string ext4
d-i partman/confirm_write_new_label boolean true
d-i partman/confirm boolean true
d-i partman/confirm_nooverwrite boolean true
d-i partman-md/confirm_nooverwrite boolean true

It is perfect.

Fails on Nextbook and probably every other device which has a flash "drive" because those come up as /dev/mmcblk0. I don't know why, but the startup does not put them under the sd path.

Tried the cheap cheat of:

d-i partman-auto/disk string /dev/discs/disc0/disc

Fails miserably in VM because under Oracle VirtualBox the "mapper" drive shows up before /dev/sda.

Has anyone found a way around this problem?

---

