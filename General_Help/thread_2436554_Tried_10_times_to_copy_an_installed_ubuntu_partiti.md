---
title: "Tried 10 times to copy an installed ubuntu partition to a USB drive - never boots"
date: 2020-02-08
forum: General Help
---

### Post by palex1919 on 2020-02-08
What I am trying to achieve is this:

Copy a Ubuntu partition (spent a bunch of time setting this one up like I wanted) to a USB stick so that I can take it with me and boot into my environment.

I tried DD, I tried clonezilla live... also installed grub manually onto the stick. IT WILL NOT BOOT on any other machine but strangely on the machine I created it on it does show
up in grub boot loader and I can boot it...????

---

### Post by HermanAB on 2020-02-08
Well, a USB widget doesn't work the same as a HDD...

However, there are special tools that will help you do what you want.  

Here is one:
[https://vitux.com/how-to-create-a-bootable-usb-stick-from-the-ubuntu-terminal/](https://vitux.com/how-to-create-a-bootable-usb-stick-from-the-ubuntu-terminal/)
(I haven't tried it)

---

### Post by oldfred on 2020-02-08
UEFI or BIOS boot.
You cannot copy gpt partitions with dd. Gpt has GUID in partition table, partition and backup partition table that must match.

May be easier just to do a new install, but partition in advance if UEFI to have the ESP. Then copy ESP from internal drive to external and copy /home. If you set up a bash file with your rsync copy of /home and anything else you want, then you can easily re-run that to refresh your flash drive.

---

### Post by kurt18947 on 2020-02-08
If I understand correctly what you're trying to accomplish, an upcoming version of Systemd looks like it might do what you want.

[https://www.phoronix.com/scan.php?page=news_item&px=Systemd-Homed-Merged](https://www.phoronix.com/scan.php?page=news_item&px=Systemd-Homed-Merged)

---

