---
title: "Expanding Disk - GParted"
date: 2020-01-02
forum: General Help
---

### Post by akio74 on 2020-01-02
Greetings! I'm trying to expand the disk on an Ubuntu host from 200GB to 400GB. After following some information online, I used GParted do to this. It appears the overall partition was expanded successfully, however there's a Block Device (Filesystem?) which still shows the original size. Attached are 3 screenshots. Any tips or advise on how to apply the expanded partition size to the Filesystem Block Device? Thanks!

Ubuntu 18.04.3 LTS

---

### Post by oldfred on 2020-01-02
Do not know LVM, but gparted is just for standard partitions, not LVM volumes.

       How to: Mount & Resize an Encrypted Partition (LUKS) also mount for repairs
[http://ubuntuforums.org/showthread.php?p=4530641](http://ubuntuforums.org/showthread.php?p=4530641)
sudo apt-get update && sudo apt-get install lvm2 cryptsetup
How to Resize a LUKS Encrypted File System.
[http://ubuntuforums.org/showthread.php?t=726724](http://ubuntuforums.org/showthread.php?t=726724)

---

### Post by Dennis N on 2020-01-02
Check free space (shows extents and GB free) in ubuntu_vg volume group:
```
sudo vgdisplay /dev/ubuntu_vg | grep -i free
```

To add all free space to the root logical volume:
```
sudo lvextend -r --extents +100%FREE /dev/ubuntu_vg/root
```

---

### Post by akio74 on 2020-01-02
I was able to get that partition extended by running the following: 

sudo lvextend -L +200G /dev/ubuntu-vg/root
sudo resize2fs /dev/ubuntu-vg/root

Thanks

---

### Post by TheFu on 2020-01-02
```
sudo lvextend -L +200G /dev/ubuntu-vg/root
sudo resize2fs /dev/ubuntu-vg/root
```
could be done in 1 command.
```
sudo lvextend -r -L +200G /dev/ubuntu-vg/root
``` The added option will resize the file system. From the manpage:

```
       -r, --resizefs
              Resize underlying filesystem together with  the  logical  volume
              using fsadm(8).

```

However, the root LV really should be limited to 25G in size and other LVs should be created for other storage needs where and when needed.  For example, /home and /var commonly would get their own LVs based on certain needs. (I didn't check the images).

The quick overview of LVM is easy to see using 3 commands:
```
sudo pvs
sudo vgs
sudo lvs
```
The old-style vgdisplay, lvdisplay, pvdisplay tools do provide much more information, but it is seldom needed and much harder to read, IMHO.

---

