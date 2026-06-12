---
title: "losetup unable to access file"
date: 2012-11-28
forum: General Help
---

### Post by mlb299 on 2012-11-28
Hello,
I am new to ubuntu but have managed to set up a dual boot windows/ubuntu machine to make use of open source forensic software.

I am trying to associate a loop device to an image using 
```

sudo losetup -r -o 32256 /dev/loop0 /home/mario/mount_points/ewf/ewf1

```
the result is 
```

/home/mario/mount_points/ewf/ewf1: Permission denied

```
even though the images permissions and ownership are  
```

-r--r--r-- 1 mario mario 10737418240 Nov 29 03:42 ewf1

```
is there something I need to do to use losetup.

---

