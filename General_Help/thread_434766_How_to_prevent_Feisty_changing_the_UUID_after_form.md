---
title: "How to prevent Feisty changing the UUID after formatting??"
date: 2007-05-06
forum: General Help
---

### Post by kilou on 2007-05-06
Hi,

I'm backing up my system in a tar file and usually the restore is just about formatting the root partition and extracting the tar archive from a LiveCD. This has worked many times but now that I'm on Feisty, each time I format my root partition to make it clean before restoring the system, Ubuntu seems to change the UUID of that partition. It means that when I boot back on the restored system, it hangs at the boot screen because the UUID in /etc/fstab and /boot/grub/menu.lst do not match the new assigned ones.

I always have to modify these 2 files so that the system can be booted. Not a big deak but I'd prefer if it was possible to prevent Feisty from changing the UUID of partitions when those are formatted. I don't know why it is so because I'm not changing the geometry of the partition, I'm just formatting with mkfs.ext3 /dev/sda1

Why does Feisty need UUID while it could recognize partition like /dev/sdaX etc??? Is there a way to prevent Feisty from changing the UUID or is it possible to customize my backup script so that I can update fstab and menu.lst automatically with the newly assigned UUID??

Thanks

---

### Post by cookfromfrozen on 2007-05-06
Personally I don't let it use UUIDs and I change any references to UUIDs in /etc/fstab and /boot/grub/menu.lst to their respective device names (/dev/hda1 etc.).

You can read the UUID of a partition with **vol_id /dev/[h|s]daX**

You can change it like this:

```
vol_id -u "6cb05fa8-fbde-11db-8314-0800200c9a66" /dev/[h|s]daX
```

---

### Post by kilou on 2007-05-06
Hi cookfromfrozen,

I'm trying to achieve the same as what you did by removing the UUID and using /dev/sda etc in both menu.lst and fstab. However when I do this Ubuntu hangs on the bootscreen :( 

My root partition is /dev/sda1 and it's current UUID is 94a41556-a573-4e62-884a-d6bad0896826. Below you can see the changes I applied to the kernel command in menu.lst and in fstab (BEFORE is with UUID and AFTER is after I change the reference to the /dev format).

Menu.lst:
-----------

BEFORE: kernel		/boot/vmlinuz-2.6.20.3-ubuntu1-custom [COLOR="Red"]root=UUID=94a41556-a573-4e62-884a-d6bad0896826[/COLOR] ro quiet splash

AFTER: kernel		/boot/vmlinuz-2.6.20.3-ubuntu1-custom [COLOR="Red"]root=/dev/sda1[/COLOR] ro quiet splash


Fstab:
-------

BEFORE: 
# /dev/sda1
[COLOR="Red"]UUID=94a41556-a573-4e62-884a-d6bad0896826[/COLOR] /               ext3    defaults,errors=remount-ro 0       1

AFTER:
[COLOR="Red"]/dev/sda1[/COLOR]  /               ext3    defaults,errors=remount-ro 0       1


The BEFORE situation works for now but if I reformat the partition the UUID is changed is my backup need to be adjusted. The AFTER situation is supposed to work but when I boot with these mods the boot process hangs.

Could you please post extracts of your menu.lst and fstab so that I can see where I'm doing something wrong?

Thanks!

---

### Post by kilou on 2007-05-06
anyone know if I've made errors in the AFTER lines??

---

### Post by kilou on 2007-05-07
Should I do **sudo update-grub** to apply changes to menu.lst????

---

### Post by jimbob on 2007-05-07
Don't know if this will help but you can quickly get the current UUID's of all drives on your system via the command [COLOR="Blue"]blkid[/COLOR]
________________________________       
  If I can't be Mr. Root I won't play ...

[COLOR="Red"][SIZE="1"]*Registered Linux User #400396*[/SIZE][/COLOR]

---

### Post by rai4shu2 on 2007-05-07
I don't think you need to update-grub just for that. Here's a snip from my Debian menu.lst:

```
title           Debian GNU/Linux, kernel 2.6.18-4-amd64
root            (hd0,4)
kernel          /boot/vmlinuz-2.6.18-4-amd64 root=/dev/hdb5 ro 
initrd          /boot/initrd.img-2.6.18-4-amd64
savedefault
```

---

### Post by kilou on 2007-05-07
Thanks!! It's working now, I did the same thing as yesterday but for some reasons now it works....

---

