---
title: "Modifying fstab"
date: 2008-04-17
forum: General Help
---

### Post by t4ggs on 2008-04-17
Hi there

this is my current fstab

proc /proc proc defaults 0 0
# Entry for /dev/sdb7 :
UUID=017ba9a4-7118-434c-923b-2ea1beb87314 / ext3 defaults,errors=remount-ro 0 1
# Entry for /dev/sda1 :
UUID=F2A8085BA80820A9 /media/sda1 ntfs-3g defaults,locale=C,locale=es_ES.utf8 0 1
# Entry for /dev/sdb5 :
UUID=C53008BF82A12446 /media/sdb5 ntfs-3g defaults,locale=C,locale=es_ES.utf8 0 1
# Entry for /dev/sdb6 :
UUID=2DAD34E22227FDBC /media/sdb6 ntfs-3g defaults,locale=C,locale=es_ES.utf8 0 1
# Entry for /dev/sdb8 :
UUID=3e80d6b5-5645-42cb-b69d-bf4d5555e0c4 none swap sw 0 0
/dev/scd0 /media/cdrom0 udf,iso9660 user,noauto,exec 0 0

And i want to modify it so my ntfs partitions could be mounted so I could acces my files in othe languages for example in Hebrew and spanish.... could someone explain to me how do i do this...and why it is so complicated...im trying yo move to ubuntu but there are things this that are still hard for me to do...

Thanks in advantage

---

### Post by Diabolis on 2008-04-17
What do you mean by accesing your files in other languages? like translating them?

---

### Post by Ziggy72 on 2008-04-18
I really don't know what you want to do, but since you have locale=es on fstab for /dev7/sda1, I'm assuming that for some reason you aren't able to mount, e.g., /dev/sda1 and that is what you want to do. If so, do the following:
```
sudo mkdir /media/sda1
sudo mount -a

```

If that works, when you reboot /dev/sda1 will (or should be) mounted automatically. if that doesn't happen, do the following
```

sudo gedit /etc/fstab

```
and change the line 
> 
UUID=F2A8085BA80820A9 /media/sda1 ntfs-3g defaults,locale=C,locale=es_ES.utf8 0 1
to> 
/devsda1 /media/sda1 ntfs-3g defaults,locale=C,locale=es_ES.utf8 0 1

Save and reboot.

If that works, just repeat the above for any other partitions you want to mount. Good luck:)

---

