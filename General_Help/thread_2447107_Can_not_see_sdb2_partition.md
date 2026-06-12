---
title: "Can not see sdb2 partition"
date: 2020-07-12
forum: General Help
---

### Post by raleigh3 on 2020-07-12
I can not see this sdb2 directory when I use thunar /media/andy/MAXTOR_SDB2/.

It said "Failed to open media/andy/Maxtor_SDB2/.

Do I need to make a change in fstab?


```
UUID=81353260-b5a5-4b72-9fce-432e7c620fdc / ext4 errors=remount-ro 0 1

UUID=b3b0f384-9e2e-45f5-8995-932f1113f59d /media/storagedrive/ ext3 defaults 0

/swapfile none swap sw 0 0

blkid
/dev/loop0: TYPE="squashfs"
/dev/loop1: TYPE="squashfs"
/dev/loop2: TYPE="squashfs"
/dev/loop3: TYPE="squashfs"
/dev/loop4: TYPE="squashfs"
/dev/loop5: TYPE="squashfs"
/dev/loop6: TYPE="squashfs"
/dev/loop7: TYPE="squashfs"
/dev/sda1: UUID="81353260-b5a5-4b72-9fce-432e7c620fdc" TYPE="ext4" PARTUUID="87fb6afb-01"
/dev/sdb1: LABEL="MAXTOR_SDB1" UUID="b3b0f384-9e2e-45f5-8995-932f1113f59d" TYPE="ext3" PARTUUID="000f0791-01"
/dev/sdb2: LABEL="MAXTOR_SDB2" UUID="e0dadb1c-0161-4862-8e95-7c42d8f7fb03" SEC_TYPE="ext2" TYPE="ext3" PARTUUID="000f0791-02"
```

---

### Post by GhX6GZMB on 2020-07-12
What does lsblk say?

---

### Post by raleigh3 on 2020-07-12
```
NAME   MAJ:MIN RM   SIZE RO TYPE MOUNTPOINT
loop0    7:0    0    55M  1 loop /snap/core18/1754
loop1    7:1    0  15.2M  1 loop /snap/ubuntu-mate-welcome/420
loop2    7:2    0   7.9M  1 loop /snap/pulsemixer/250
loop3    7:3    0  14.9M  1 loop /snap/ubuntu-mate-welcome/539
loop4    7:4    0    16K  1 loop /snap/software-boutique/39
loop5    7:5    0    16K  1 loop /snap/software-boutique/54
loop6    7:6    0  89.1M  1 loop /snap/core/8268
loop7    7:7    0   7.9M  1 loop /snap/pulsemixer/283
loop8    7:8    0  96.5M  1 loop /snap/core/9436
sda      8:0    0   1.8T  0 disk 
&#9492;&#9472;sda1   8:1    0   1.8T  0 part /
sdb      8:16   0 298.1G  0 disk 
&#9500;&#9472;sdb1   8:17   0  98.4G  0 part /media/storagedrive
&#9492;&#9472;sdb2   8:18   0 199.7G  0 part 
sr0     11:0    1  1024M  0 rom
```

---

### Post by jp734 on 2020-07-12
Have you tried manually mounting the volume before viewing it on thunar? If your fstab only contains those two lines, you might need to type an entry for your /dev/sdb2

---

### Post by raleigh3 on 2020-07-13
Thanks. 

This entry fixed the problem.

UUID=e0dadb1c-0161-4862-8e95-7c42d8f7fb03 /media/andy/MAXTOR_SDB2            ext3    defaults 0

---

