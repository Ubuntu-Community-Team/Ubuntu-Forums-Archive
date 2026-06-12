---
title: "sda3 has not full space? fdisk problem"
date: 2022-10-28
forum: General Help
---

### Post by untidy4732 on 2022-10-28
Hello!

On my Ubuntu - vServer I only have ~18GB disc space but it should be ~36GB.

sudo lsblk -o NAME,FSTYPE,SIZE,MOUNTPOINT,LAB  shows me:



```
sda                                   38,1G
&#9500;&#9472;sda1                                   1M
&#9500;&#9472;sda2                    ext4           2G /boot
&#9492;&#9472;sda3                    LVM2_member 36,1G
  &#9492;&#9472;ubuntu--vg-ubuntu--lv ext4        18,1G /
sr0                                   1024M

```
Is it possible to get all my Discpsace to the system partition of ubunut? or how else can i access it the rest of the 36gb?

Thanks for your help

---

### Post by MAFoElffen on 2022-10-28
The LV is not grown as large as the VG.

Example commands, adjusted to the output you get along the way, and how large you want to grow it...
```

sudo -i
pvs
pvdisplay
vgs
vgdisplay
lvs
lvdisplay
lvextend -l +100%FREE /dev/vg_name/lv_name 

```

---

### Post by untidy4732 on 2022-10-28
Hey, thanks for your reply and also the exact commands - I appreciate it!

Now I got the following output

sda                                   38,1G
&#9500;&#9472;sda1                                   1M
&#9500;&#9472;sda2                    ext4           2G /boot
&#9492;&#9472;sda3                    LVM2_member 36,1G
  &#9492;&#9472;ubuntu--vg-ubuntu--lv ext4        36,1G /


Looks gut, BUT i can't access it.
df -h just show me the 18g

Filesystem                         Size  Used Avail Use% Mounted on
tmpfs                              193M  2,1M  191M   2% /run
/dev/mapper/ubuntu--vg-ubuntu--lv   18G   12G  4,8G  72% /
tmpfs                              964M     0  964M   0% /dev/shm
tmpfs                              5,0M     0  5,0M   0% /run/lock
/dev/sda2                          2,0G  246M  1,6G  14% /boot

---

### Post by ActionParsnip on 2022-10-28
what is the output of
```

vgs
lvs

```

---

### Post by untidy4732 on 2022-10-28
```

VG        #PV #LV #SN Attr   VSize  VFree
  ubuntu-vg   1   1   0 wz--n- 36,14g    0


 LV        VG        Attr       LSize  Pool Origin Data%  Meta%  Move Log Cpy%Sync Convert
  ubuntu-lv ubuntu-vg -wi-ao---- 36,14g

```

---

### Post by ActionParsnip on 2022-10-28
Have you recently resized the ubuntu-lv logical volume to use the full space? Sounds like you just need to resize the ext4 into the new space. Try:
```

resize2fs /dev/mapper/ubuntu--vg-ubuntu--lv

```

---

### Post by untidy4732 on 2022-10-28
Nope - it's a clean installation from a Hoster!

The last command led to the final success. Thank you very much - now everything is ok :)
I really thank you for your help.

---

### Post by ActionParsnip on 2022-10-28
Please mark as solved. You have an LVM based file system with unassigned space. The df output shows only the file system. You had to extend your file system into the new allocated space.

---

