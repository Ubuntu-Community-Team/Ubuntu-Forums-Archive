---
title: "Dual boot problem"
date: 2008-05-08
forum: General Help
---

### Post by CLomax on 2008-05-08
After upgrading to 8.04 I have been unable to boot into my Windows partition (Vista, if that's important). /boot/grub/menu.lst seems O.K since I used the exact same configuration for 7.10.
> ## ## End Default Options ##

title		Windows Vista
root		(hd0,0)
savedefault
chainloader	+1

title		Ubuntu 8.04
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.24-16-generic root=UUID=3c7d5ff6-b716-499a-9bb8-9fcc8e021a35 ro quiet splash
initrd		/boot/initrd.img-2.6.24-16-generic
quiet

title		Ubuntu 8.04 Recovery Mode
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.24-16-generic root=UUID=3c7d5ff6-b716-499a-9bb8-9fcc8e021a35 ro single
initrd		/boot/initrd.img-2.6.24-16-generic

title		Ubuntu 8.04 memtest86+
root		(hd0,1)
kernel		/boot/memtest86+.bin
quiet

So when attempting to access Windows it shows something along the lines of, "Loading grub stage 2" for a few milliseconds and returns to the OS menu.
If you'd like more information, ask.

I appreciate any help, thank you.

---

### Post by didac on 2008-05-08
Sounds strange. Try adding


```
makeactive
```

to the Windows Vista option in /boot/grub/menu.lst

Also, check 

```
sudo fdisk -l
```

just to make sure Vista is your first partition.

Full grub information in

[http://users.bigpond.net.au/hermanzone/p15.htm#Operating_system_Entries](http://users.bigpond.net.au/hermanzone/p15.htm#Operating_system_Entries)

---

