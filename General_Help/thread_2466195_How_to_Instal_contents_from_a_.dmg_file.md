---
title: "How to Instal contents from a .dmg file"
date: 2021-08-22
forum: General Help
---

### Post by Rick St. George on 2021-08-22
Did a search, but found nothing regarding this issue.

v20.04 ... Attempting to install contents of a .DMG file, which is a Trading Platform, and get the following;

```

MS-7640: ~cd /home/stephen/Downloads
MS-7640:~/Downloads$ sudo mount -t hfsplus IraCharts-setup.dmg /mnt
 
mount: /mnt: wrong fs type, bad option, bad superblock on /dev/loop0, missing codepage or helper program, or other error.
stephen@stephen-MS-7640:~/Downloads$ dmg2img IraCharts-setup.dmg IraCharts-setup.img

dmg2img v1.6.7 (c) vu1tur (to@vu1tur.eu.org)

IraCharts-setup.dmg --> IraCharts-setup.img


decompressing:
opening partition 0 ...             100.00%  ok
opening partition 1 ...             100.00%  ok
opening partition 2 ...             100.00%  ok
opening partition 3 ...             100.00%  ok
opening partition 4 ...             100.00%  ok
opening partition 5 ...             100.00%  ok
opening partition 6 ...             100.00%  ok
opening partition 7 ...             100.00%  ok

Archive successfully decompressed as IraCharts-setup.img
MS-7640:~/Downloads$ sudo mkdir /mnt/IraCharts
MS-7640:~/Downloads$ sudo modprobe hfsplus
modprobe: FATAL: Module hfspllus not found in directory /lib/modules/5.11.0-27-lowlatency

MS-7640:~/Downloads$ sudo mount -t hfsplus -o loop IraCharts-setup.img /mnt/IraCharts
mount: /mnt/IraCharts: wrong fs type, bad option, bad superblock on /dev/loop0, missing codepage or helper program, or other error.


```

What am I doing wrong?

---

### Post by shantiq on 2021-08-22
maybe av a look [here]("https://askubuntu.com/questions/38112/how-can-i-open-a-dmg-file")

---

### Post by Rick St. George on 2021-08-22
Thanks Shantiq, but I followed all but the 7z extraction. I can mount it and see the files.
However, it may not work as this file is for installation onto a MAC, (although linux based) is not for Ubuntu.
Will contact my Broker for another possible solution. They ONLY have a Win.exe and this MAC.dmg file.

---

