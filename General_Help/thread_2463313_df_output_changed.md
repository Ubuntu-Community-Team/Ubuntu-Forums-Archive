---
title: "df output changed"
date: 2021-06-08
forum: General Help
---

### Post by anneranch on 2021-06-08
What gives ?
Please note  next to last entry - why did the **":humanly  reliable"  display changed BY ITSELF .**
( YES i  know where  to change it ) 


```
qe@qe-desktop:~$ df
 Filesystem     1K-blocks     Used Available Use% Mounted on
 tmpfs             784256     2272    781984   1% /run
 /dev/sdc5      163746596 11468620 143890392   8% /
 tmpfs            3921264        0   3921264   0% /dev/shm
 tmpfs               5120        4      5116   1% /run/lock
 tmpfs               4096        0      4096   0% /sys/fs/cgroup
 /dev/sda1         523248     5348    517900   2% /boot/efi
 tmpfs             784252     1480    782772   1% /run/user/1000
 /dev/sdi13     143611004 41925424  94320820  31% /media/qe/QT_COPY
 qe@qe-desktop:~$ 
``` 
 
```
 e@qe-desktop:~$ df
 Filesystem     1K-blocks     Used Available Use% Mounted on
 tmpfs             784256     2180    782076   1% /run
 /dev/sdc5      163746596 11561540 143797472   8% /
 tmpfs            3921264     9840   3911424   1% /dev/shm
 tmpfs               5120        4      5116   1% /run/lock
 tmpfs               4096        0      4096   0% /sys/fs/cgroup
 /dev/sda1         523248     5348    517900   2% /boot/efi
 /dev/sdh13     143611004 41925424  94320820  31% /mnt/usb-Seagate_BUP_Ultra_Touch_00000000NAB133HH-0:0-part13
 tmpfs             784252      124    784128   1% /run/user/1000
 qe@qe-desktop:~$
```

---

### Post by deadflowr on 2021-06-08
Because you've unmounted one device and mounted a new one somewhere else.

I'm not sure if it's relevant but I see that the /media directory mounts are always listed last.
If none exist then the tmpfs /run/user/1000+ are listed last.
Edit: But that might just be because of the ordering of when things were mounted.

---

### Post by oldfred on 2021-06-08
My NVMe drive is listed last.
And my USB drives that may be a high letter become sda on a reboot.
That is why you cannot rely on device like /dev/sdc to run commands. And why fstab now recommends using UUID or label (that you make sure are different) that are unique.

---

### Post by anneranch on 2021-06-08
Because you've unmounted one device and mounted a new one somewhere else.

Just noticed  that the mount points also changed.

---

