---
title: "Auto re-install grub every boot?"
date: 2006-11-05
forum: General Help
---

### Post by irw on 2006-11-05
I have a HP Pavillion dv8000 laptop which contains 2 SATA hard drives. Dual boot with Windows on sda1 and Edgy Ubuntu on sdb1, with a number of other partitions as well.

I have a random problem of grub coming up with an error 17 every so often. I then use a USB key with grub on to get into Ubuntu, then reinstall grub.  It always works fine for a few times after doing this, but eventually I get the error again.

The series of commands I use are:```
sudo grub

root (hd1,0)

setup (hd0)

quit
```


I am wondering if it may be worth trying a script to run every time I boot or shut down to re-write grub.  My problem is I do not know how to create such a script - I have cut and pasted to produce simple scripts in the past, but how would I get the last 3 commands into grub?

Alternatively is there any other way around this??

---

### Post by bulldog on 2006-11-05
You can setup GRUB on the Edgy hdd and make this your bootdevice.
Reinstall your windows bootloader with the windows cd and the recovery console [fixmbr/fixboot]

Than map your windows entry in GRUB and you can always boot into windows without GRUB.

To map your windows make your windows entry like this,```
### END DEBIAN AUTOMAGIC KERNELS LIST


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/hda1
title		Microsoft Windows XP Professional
map (hd0,0) (hd1,0)
map (hd1,0) (hd0,0)
rootnoverify (hd0,0)
savedefault
makeactive
chainloader	+1

```

---

### Post by jd65pl on 2006-11-05
Grub error 17 means that the partition has been detected by grub boot but it can't determin the partition type. Just for information.

---

### Post by irw on 2006-11-05
Thanks for the rapid responses.

I found out what the error means, but despite extensive searches no real answer to why it occurs randomly; re-installing grub seems to fix it - it works, so further logic discarded for the time being!

Bulldog - it maybe it is late and I need to go to bed, but could explain how that works?

---

