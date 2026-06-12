---
title: "LVM error"
date: 2019-08-22
forum: General Help
---

### Post by led0b on 2019-08-22
[COLOR=#000000][FONT=Arial]Hello,
i made an ubuntu18.04 server installation with  lvm.
A vg use all the hardisk space 120G
Installation made a small lv for the /
I manual made a 100G lv for my vms in VG and extend ubuntu lv to 20G.

Recently, i have some problems with some command-line with message error " No space left on device"

i do a df command and the ubuntu-lv is used fully but the size is not 20G.

I don't understand the mistake. Have you any explanation ?G ?[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]
[B]udev                                6113908       0   6113908   0% /dev
tmpfs                               1229004   86576   1142428   8% /run
/dev/mapper/ubuntu--vg-ubuntu--lv   4062912 4046528         0 100% /
tmpfs                               6145004       0   6145004   0% /dev/shm
tmpfs                                  5120       0      5120   0% /run/lock
tmpfs                               6145004       0   6145004   0% /sys/fs/cgroup
/dev/sda2                            999320   77932    852576   9% /boot
/dev/loop0                            93184   93184         0 100% /snap/core/6350
tmpfs                               1229000       0   1229000   0% /run/user/1000
/dev/loop1                            90880   90880         0 100% /snap/core/7396
/dev/mapper/ubuntu--vg-kvm--lv     30832548 9330608  19912692  32% /mnt/kvm[/B][/FONT][/COLOR][COLOR=#000000][FONT=Arial]
[/FONT][/COLOR]

---

### Post by Dennis N on 2019-08-22
```
/dev/mapper/ubuntu--vg-ubuntu--lv 4062912 4046528 0 100% /

```
The units of measurement used are not included in your post, but if it's the same units as my machine, its measured in 1K blocks. Roughly, your reported file system size is equivalent to 4 GB.

If so, you possibly didn't include an option to expand the file system when you extended the LV to 20GB. What exact command did you use?

---

### Post by led0b on 2019-08-22
I do this command line :
**sudo lvextend -L 20G /dev/ubuntu-vg/ubuntu-lv**

---

### Post by Dennis N on 2019-08-22
> **ronny-caron said:**
> I do this command line :
**sudo lvextend -L 20G /dev/ubuntu-vg/ubuntu-lv**

It should have been:

```
sudo lvextend --resizefs -L 20G /dev/ubuntu-vg/ubuntu-lv
```

Run it again, with the --resizefs option included.

---

### Post by led0b on 2019-08-22
In first time, this command did an error because the freespace is too small. I cleaned apt cache and did it again and it successfull.
Thanks a lot.

---

