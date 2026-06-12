---
title: "installing driver/system freezes/now wont boot!"
date: 2013-01-23
forum: General Help
---

### Post by oxf on 2013-01-23
Heres what happened;

 I installed Lubuntu 12.04 on new partition. After running updates I went to Hardware Drivers and started to activated the Cedartrail proprietary graphics driver. Before it was finished downloading the laptop froze up and I had no option but to kill the power. Now if I try to boot into that partition it gets about halfway through the process and gives a load of error messages and stalls, thats it.

I can boot from the Live USB and recovery mode too (and from Ubuntu in the other partition) Is there a way I can boot from either of these to allow me to reinstall the driver or repair it so I can boot normally again?

Thanks
Caitlin

---

### Post by oxf on 2013-01-24
Help!

---

### Post by steeldriver on 2013-01-24
I don't know anything about the cedarview packages specifically, but you should be able to repair / remove / reinstall any packages manually from the recovery console

You will need to remount the filesystem with read-write permissions first:

```
# mount -o remount,rw /
```(NB - no space between the 'remount,rw' options) and then I'd suggest checking the package status

```
# dpkg -l | grep cedar
```(that's a lowercase 'ell'). Depending on the result of that you can either attempt to reinstall or fix (-f) with apt-get.

---

### Post by oxf on 2013-01-25
Thanks, that seem to have taken care of it! :D

---

