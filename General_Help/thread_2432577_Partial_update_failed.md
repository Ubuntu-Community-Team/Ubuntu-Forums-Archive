---
title: "Partial update failed"
date: 2019-12-04
forum: General Help
---

### Post by sniper8752 on 2019-12-04
I received this error after performing a upgrade on my system: 
```
update-initramfs: Generating /boot/initrd.img-4.4.0-170-generic/etc/kernel/postinst.d/zz-update-grub:
Generating grub configuration file ...
Found linux image: /boot/vmlinuz-4.4.0-170-generic
Found initrd image: /boot/initrd.img-4.4.0-170-generic
Found linux image: /boot/vmlinuz-4.4.0-169-generic
Found initrd image: /boot/initrd.img-4.4.0-169-generic
Found linux image: /boot/vmlinuz-4.4.0-168-generic
Found initrd image: /boot/initrd.img-4.4.0-168-generic
Found linux image: /boot/vmlinuz-4.4.0-166-generic
Found initrd image: /boot/initrd.img-4.4.0-166-generic
Found memtest86+ image: /memtest86+.elf
Found memtest86+ image: /memtest86+.bin
done
Processing triggers for initramfs-tools (0.122ubuntu8.16) ...
update-initramfs: Generating /boot/initrd.img-4.4.0-170-generic


gzip: stdout: No space left on device
E: mkinitramfs failure cpio 141 gzip 1
update-initramfs: failed for /boot/initrd.img-4.4.0-170-generic with 1.
dpkg: error processing package initramfs-tools (--configure):
 subprocess installed post-installation script returned error exit status 1
Errors were encountered while processing:
 initramfs-tools
```
I did an autoremove, which made some room, then "sudo update-grub".  Does this resolve the previous error?

---

### Post by Bashing-om on 2019-12-04
sniper8752: Welp -

> 
gzip: stdout: No space left on device


Probable that this will not work to resolve, as no headroom - but, 
try:
```

sudo apt --purge autoremove

```

else we have to roll up the sleeves and goto manual work.

[INDENT][INDENT]there is a way
[/INDENT][/INDENT]

---

### Post by sniper8752 on 2019-12-06
[COLOR=#000000][INDENT]I did an autoremove, which made some room, then "sudo update-grub". Does this resolve the previous error?[/INDENT]


[/COLOR]

---

### Post by Bashing-om on 2019-12-06
sniper8752: well ....

> 
Does this resolve the previous error?


Very likely :D

What shows
```

df -h
df -i
sudo dpkg -l | grep linux-
sudo apt update
sudo apt upgrade

```

[INDENT][INDENT]All in the process
[/INDENT][/INDENT]

---

