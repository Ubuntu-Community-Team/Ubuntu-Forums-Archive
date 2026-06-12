---
title: "windows and ubuntu"
date: 2008-02-29
forum: General Help
---

### Post by naveedahmed on 2008-02-29
i have installed windows in a logical drive previously .now i installed ubuntu 7.10 in a primary partition. the OS is not able to recognise windows at boot time.is there any way through which i can regain windows in the boot menu. i have only made one pirmary partition in which i installed linux.

---

### Post by pointone on 2008-02-29
From what I remember, Windows is a bit pissy and won't boot from an extended partition. In fact, I think Windows needs to be installed on the first partition of a drive. I haven't messed with it for a while, though, so I could be wrong.

---

### Post by fede on 2008-02-29
I had the same idea as pointone, yet if it booted before installing Ubuntu, it should be able to boot again, I guess... 

Have you set up GRUB properly? Assuming you haven't or you don't yet know about this:

Edit /boot/grub/menu.lst as root: (backup first just in case)
```

cp /boot/grub/menu.lst /boot/grub/menu.lst.backup
gksu gedit /boot/grub/menu.lst

```

Look for this line at the end:
```
### END DEBIAN AUTOMAGIC KERNELS LIST
```

and add the following after it, **changing the value of n within "root (hd0,n)" to the appropriate partition number**: primary partitions start from 0 and "extended partitions" (really they are logical disks within the extended partition, if I uderstand correctly) start at 5. Hence, if win xp is in the first extended partition, use "root (hd0,5)"; if in the second use "root (hd0,6)", etc.

```

title Windows XP
root (hd0,n)
makeactive
chainloader +1

```

Save it and restart; then use the menu at startup to load windows xp - by default it is hidden by a message which tells you to press ESC to see boot options or something like that.

Hope it helps.

---

### Post by iscreamkid on 2008-02-29
I will echo pointone.

Use fdisk to partition your hard drive allowing space for Ubuntu.
Install Windows, get it running and updated and then load Ubuntu.

Google dual boot and read up on how to get both running. Quite a few people have posted articles on how to do it successfully.

Ubuntu will by default use GRUB to let you choose between them.

---

### Post by forrestcupp on 2008-02-29
It's true.  You really should install Windows on a primary partition.

---

