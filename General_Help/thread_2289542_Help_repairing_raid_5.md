---
title: "Help repairing raid 5"
date: 2015-08-04
forum: General Help
---

### Post by jason.doughty.jtg on 2015-08-04
[FONT=Arial][SIZE=3]Help repairing raid 5[/SIZE][/FONT]
 

 [FONT=Arial][SIZE=3]one of my HDD is making a grinding sound I believe it is  /dev/sda1 with 8000 bad sector, is this the best way to replace the HDD.[/SIZE][/FONT]
 

 [FONT=Arial][SIZE=3]sudo mdadm --manage /dev/md0 --fail /dev/sda1[/SIZE][/FONT]

[FONT=Arial][SIZE=3]sudo mdadm --manage /dev/md0 --remove /dev/sda1[/SIZE][/FONT]

[FONT=Arial][SIZE=3]shut down system replace HDD[/SIZE][/FONT]

[FONT=Arial][SIZE=3]boot and format new HDD with one ext4 partition[/SIZE][/FONT]

[FONT=Arial][SIZE=3]sudo mdadm --manage /dev/md0 --add /dev/sda1[/SIZE][/FONT]

[FONT=Arial][SIZE=3]cat /proc/mdstat[/SIZE][/FONT]

---

