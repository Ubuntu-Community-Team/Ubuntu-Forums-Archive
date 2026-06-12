---
title: "Dual boot with same OS"
date: 2020-11-13
forum: General Help
---

### Post by juraj-papic on 2020-11-13
Hello,

I have my notebook with ubuntu 19.04 (yes I have to update it) I would like to know If I can have a dual boot with ubuntu 20.x, ?


thanks.

---

### Post by oldfred on 2020-11-13
Yes.
Better then to have data (not /home) in separate partition(s), so you can use in all installs.
Most recent install is grub in control, unless you reconfigure.

I have several installs:
```
[FONT=monospace][COLOR=#54ff54]**fred@z170-focal-k**[/COLOR][COLOR=#000000]:[/COLOR][COLOR=#5454ff]**~**[/COLOR][COLOR=#000000]$ lsblk -f [/COLOR]
NAME        FSTYPE LABEL     UUID                                 FSAVAIL FSUSE% MOUNTPOINT 
sda                                                                               
&#9500;&#9472;sda1      vfat   ESP_B     F496-1330                                            
&#9500;&#9472;sda2      ext4   bionic_b  06cdd4fd-6a03-4880-9021-7febff21e4b1                 
&#9500;&#9472;sda3      ext4   ISO_b     c395f36d-5e02-4913-a904-e336054b2eff                 
&#9500;&#9472;sda4      ext4   backup_b  dd4e4a2e-4785-4441-91b0-28234b98e625                 
&#9500;&#9472;sda5      ext4   focal_a   f2cde08c-a045-43ef-83bd-a4132aa23fbd                 
&#9500;&#9472;sda6      ext4   data      f9537995-8b44-4abb-b5fb-ec27023f57b2                 
&#9500;&#9472;sda7      swap             3ef43e7c-8a35-4f8b-bc73-c91d6098d4cd                 
&#9500;&#9472;sda8      ext4   groovy    10e39ce2-ca45-4033-9038-10ba57464f83                 
&#9492;&#9472;sda9      ext4   groovy_k  6fadac33-0cdc-4005-940c-a4d035058dd8                 
nvme0n1                                                                           
&#9500;&#9472;nvme0n1p1 vfat   ESP_NVME  4954-C122                             499.1M     2% /boot/efi 
&#9500;&#9472;nvme0n1p2 ext4   focal_0   b913e1bc-6f08-4984-b653-9a604d95470a                 
&#9500;&#9472;nvme0n1p3 ext4   focal_k   54029c4f-0cbe-413e-80ce-78a4995b0551     19G    29% / 
&#9500;&#9472;nvme0n1p4 ext4             dd5925b4-0250-4f6d-b59e-165f85365721                 
&#9492;&#9472;nvme0n1p5 ext4   nvme_data 1a44f4af-6780-4bbd-ad0b-6385ed30830b   59.1G    64% /mnt/data

[/FONT]
```

---

### Post by juraj-papic on 2020-11-13
Hello this is my output

```
lsblk -f 
NAME        FSTYPE   LABEL UUID                                 FSAVAIL FSUSE% MOUNTPOINT
nvme0n1                                                                        
&#9500;&#9472;nvme0n1p1 vfat           881B-F726                             503,5M     1% /boot/efi
&#9492;&#9472;nvme0n1p2 ext4           04e66018-8845-477f-9345-111dded7f821  304,1G    30% /
```

---

### Post by oldfred on 2020-11-13
Please use code tags for longer terminal output. Easy to add in Forum's advanced editor and # icon.
Also removed snaps from list as they are not partitions. You can exclude snaps from lists:
lsblk -o NAME,FSTYPE,LABEL,MOUNTPOINT,SIZE,fsused,MODEL | egrep -v "^loop"

It looks like then you have just / (root) with about 100GB used of 300GB?

I might move all data to new partition.
You can shrink p2 to make room for new install & data partition.

You have to use gparted from live installer to resize or create partitions so all partitions are unmounted.
Then you can use Something Else to choose new / (root) partition as /. Be sure to boot in UEFI boot mode.
You have to manually add data partition to fstab after install to have it mounted when rebooting.

 [https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI)

[http://ubuntuforums.org/showthread.php?t=2315714](http://ubuntuforums.org/showthread.php?t=2315714)
Splitting home directory discussion and details:
[http://ubuntuforums.org/showthread.php?t=1811198](http://ubuntuforums.org/showthread.php?t=1811198)
[http://ubuntuforums.org/showthread.php?t=1901437](http://ubuntuforums.org/showthread.php?t=1901437)

---

### Post by juraj-papic on 2020-11-13
sorry for that!

---

