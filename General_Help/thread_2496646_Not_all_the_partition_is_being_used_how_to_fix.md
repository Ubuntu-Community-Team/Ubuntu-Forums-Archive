---
title: "Not all the partition is being used: how to fix"
date: 2024-04-06
forum: General Help
---

### Post by abasel on 2024-04-06
```
sudo lsblk -o NAME,FSTYPE,SIZE,MOUNTPOINT,LABEL
```

Gives

```
NAME                      FSTYPE       SIZE MOUNTPOINT LABEL
sr0                                   1024M
xvda                                    20G
&#9500;&#9472;xvda1                                  1M
&#9500;&#9472;xvda2                   ext4         1.8G /boot
&#9492;&#9472;xvda3                   LVM2_member 18.2G
  &#9492;&#9472;ubuntu--vg-ubuntu--lv ext4          10G /

```

I am wanting ubuntu--vg-ubuntu--lv to use all of xvda3 space available.

How do I do this?

---

### Post by abasel on 2024-04-06
Ah, I think I can simply boot using gparted disk and then expand it. Will try when back at desk.

---

### Post by Dennis N on 2024-04-06
> **abasel said:**
> Ah, I think I can simply boot using gparted disk and then expand it. Will try when back at desk.
You will find out that gparted cannot manage LVM devices. You need to use a terminal.
ubuntu-vg is your volume group - size 18.2G
ubuntu-lv is your logical volume - size 10G

One terminal command will do it:
```
sudo lvextend --resizefs --size 18.2G /dev/ubuntu-vg/ubuntu-lv
```

You can do from Ubuntu itself. That's a nice thing about LVM.

---

### Post by abasel on 2024-04-06
Awesome, thanks that worked a treat.

> **Dennis N said:**
> You will find out that gparted cannot manage LVM devices. You need to use a terminal.
ubuntu-vg is your volume group - size 18.2G
ubuntu-lv is your logical volume - size 10G

One terminal command will do it:
```
sudo lvextend --resizefs --size 18.2G /dev/ubuntu-vg/ubuntu-lv
```

You can do from Ubuntu itself. That's a nice thing about LVM.

---

