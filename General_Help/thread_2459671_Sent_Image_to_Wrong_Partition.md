---
title: "Sent Image to Wrong Partition"
date: 2021-03-23
forum: General Help
---

### Post by webmanoffesto on 2021-03-23
I downloaded an Ubuntu ISO which I wanted to send to my keychain sized  flash drive. I used one of the simple apps like USB image writer. But I  sent the image to the wrong destination, one on the laptop I was using.  That laptop has a boot partition and a data partition. How do I find out  if I did damage. I'm now using that laptop, but it won't boot, so I  booted Ubuntu Mint off a flash drive. 

When I open "Disks"
I see a 1 TB drive
Volume: /dev/sda, free space, 538MB
Volume: / dev/sda2/, 1000 GB, Ext4 

I  use an online service to backup my data. But I'm also wondering how I  can get back the data which is on this laptop, without going through  download to restore.

---

### Post by oldfred on 2021-03-23
Typically that overwrites the first approx 2.5GB (size of ISO) of your drive. And may overwrite partition table if you used a tool that uses dd to create a hybrid DVD/flash drive type installer. Then entire drive's old data may not be accessible.
Is drive gpt partitioned? That has a backup partition table an often allows recovery of partition table, but not data. Any data overwritten is gone.

It is good you have backup. Many do not. Then testdisk and/or photorec to try to recovery some data.

Post these:
sudo gdisk -l /dev/sda  # if drive is sda or change to correct drive
sudo fdisk -lu

---

### Post by HermanAB on 2021-03-23
I’m sure you already know the answer to that question...

Hope that your online backups are good.  You will find it is much easier and faster to reinstall and restore your data, than trying to recover it with photorec.

---

