---
title: "The system is running in low-graphics mode  ubuntu 14.04"
date: 2014-12-12
forum: General Help
---

### Post by ibod on 2014-12-12
Hi

I am having problems fixing the above error, have tried most of the solutions I could find in google but they did not work 

Yesterday I removed Libre Office and installed Open Office which worked well and fixed the problems i was having with Libre Office. 

This morning the system started with the message "The system is running in low-graphics mode"

Graphics card is Nvidia GeForce 8200

Have found that if I go into the grub menu and use an older kernel (3.13.0-35) then the system will boot.
I am using that boot now 

Thanks for any help anyone can give

---

### Post by schragge on 2014-12-12
What graphics driver are you using? The standard Nouveau driver that comes preinstalled with Ubuntu or proprietary Nvidia driver from restricted repository? (See [uhelp]community/BinaryDriverHowto/Nvidia[/uhelp])

---

### Post by QIII on 2014-12-12
Also, if using the proprietary driver, how did you install it?

---

### Post by ibod on 2014-12-12
This is intresting I had tried changing the driver as one of the posted fixes without any luck 

I changed it to NVIDIA binary driver - version 331.113 from nvidia-331 (proprietary, tested)

but having now booted with the 3.13.0-39 kernel (only way i can make it boot) it is listed as using 

NVIDIA legacy driver - version 304.125 from nvidia-304 (prorietary)

Instulled using aditional drivers

---

### Post by ibod on 2014-12-12
I did the driver change while booted in the 3.13.0-39 kernel but after the change i got the same "The system is running in low-graphics mode" error 

Hence I and now booting with 3.13.0-35 kernel

---

### Post by pqwoerituytrueiwoq on 2014-12-12
i would suggest installing [nvidia-current]("apt:nvidia-current")
if you installed the driver from nvidia's website remove that 1st using one of these 3 comamnds (i forgot the name of the uninstaller)
```
sudo nvidia-uninstaller
sudo nvidia-uninstall
sudo nvidia-installer --uninstall
```
i have a GEforce 8200m it likes to crash and freeze using the recent nvidia drivers

---

