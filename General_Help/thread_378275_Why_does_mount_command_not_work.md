---
title: "Why does mount command not work"
date: 2007-03-07
forum: General Help
---

### Post by wej1971 on 2007-03-07
I've had some problems with mounting a 'dirty' windows volume, and one of the suggestions is to mount as read-only, which is fine by me. Only problem is the following command doesn't work (it just shows the mount help information): -

mount -t ntfs /dev/sda1 /media/windows -ro

What is wrong with this command?

---

### Post by Kateikyoushi on 2007-03-07
Try mount /dev/sda1 /media/windows -t ntfs -ro

---

### Post by gradedcheese on 2007-03-07
If you look at 'man mount', you'll find that like most commands, mount takes options first and then arguments.  Also -o is for options like 'ro'

```

mount -t ntfs -o ro /dev/sda1 /media/windows

```

---

### Post by wej1971 on 2007-03-07
I'll try it in a different order - I got the original command from another web page which (obviously) may have been wrong ;)

---

### Post by Kateikyoushi on 2007-03-07
Oddly enough ubuntu wiki does not match with the manual either nonetheless it works. [LINK]("http://ubuntuguide.org/wiki/Ubuntu_Edgy#How_to_mount.2Funmount_Windows_partitions_.28NTFS.29_manually.2C_and_allow_all_users_to_read_only")

---

