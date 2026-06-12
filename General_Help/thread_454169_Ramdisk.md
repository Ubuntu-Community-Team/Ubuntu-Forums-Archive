---
title: "Ramdisk"
date: 2007-05-25
forum: General Help
---

### Post by atlfalcons866 on 2007-05-25
hey guys
I am starting to love ubuntu a lot more everyday:razz: Is there a way to set up a ram disk?

---

### Post by mannheim on 2007-05-25
I think the linux kernel creates some ram disks for you at boot time. But they aren't formatted or mounted, and because of the magic of linux memory management they don't cost you anything in terms of ram space until you start using them.

You start using a ram disk by doing something like
```

sudo mke2fs /dev/ram0
sudo mkdir /mnt/mountpoint
sudo mount /dev/ram0 /mnt/mountpoint

```

You will then have a ram disk formatted with the e2fs mounted at /mnt/mountpoint. By default, it will be 65M in size. To make it bigger, you need to change a boot parameter in grub, I believe.

---

