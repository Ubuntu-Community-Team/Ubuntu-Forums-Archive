---
title: "Grub error 15"
date: 2007-09-27
forum: General Help
---

### Post by Niall Flinn on 2007-09-27
Hi,

I know this has come up before, but I can't seem to fix it:

I did an update on my system (edgy) and, as before, it has screwed up grub, or /boot/grub/menu.lst 

Now when I boot, I get an 'error 15: file not found'

My system has the following hard drives:

```
/dev/hda1
/dev/hdc1
/dev/hdc4
/dev/hdc3
/dev/sda1
/dev/sda2

```

And my menu.lst looks like this:


```
title		Ubuntu, kernel 2.6.17-12-generic
root		(hd1,0)
kernel		/boot/vmlinuz-2.6.17-12-generic root=/dev/hdc1 ro quiet splash
initrd		/boot/initrd.img-2.6.17-12-generic
quiet
savedefault
boot
```

So, if I understand it correctly, it should be loading vmlinuz from the first partition of the second drive in the machine (hdc1)?

Does anyone know why I can't boot? Oddly enough, I can get it to boot using the boot menu on an install CD. 

Thanks,

Niall

---

### Post by oldos2er on 2007-09-27
Maybe give this a try: [http://ubuntuforums.org/showthread.php?t=224351](http://ubuntuforums.org/showthread.php?t=224351)

---

