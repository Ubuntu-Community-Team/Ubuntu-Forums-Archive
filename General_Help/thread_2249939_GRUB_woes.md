---
title: "GRUB woes"
date: 2014-10-25
forum: General Help
---

### Post by mayagrafix on 2014-10-25
After installing Lubuntu 14.04 Mini ISO (which is more of a server OS) GRUB appears at start up asking which OS I want to use (Lubuntu or Ubuntu 14.04 LTS). Problem is, there is only 1 OS installed on the sda hard drive.

The phantom OS is supposedly on sdb1. Gparted shows no other partitions/devices on the HDD, only the normal sda1, sda2 and linux-swap sda5.

When I edit GRUB (sudo gedit /etc/default/grub) settings, there is no reference to any other OS or devices to comment out. Is there another GRUB settings doc I should be editing? Can I just turn off GRUB since there is only 1 OS on HDD/device sda?

Thanks for any and all help :<)

---

### Post by Bashing-om on 2014-10-25
mayagrafix; Hello,

> **mayagrafix said:**
> After installing Lubuntu 14.04 Mini ISO (which is more of a server OS) GRUB appears at start up asking which OS I want to use (Lubuntu or Ubuntu 14.04 LTS). Problem is, there is only 1 OS installed on the sda hard drive.

The phantom OS is supposedly on sdb1. Gparted shows no other partitions/devices on the HDD, only the normal sda1, sda2 and linux-swap sda5.

When I edit GRUB (sudo gedit /etc/default/grub) settings, there is no reference to any other OS or devices to comment out. Is there another GRUB settings doc I should be editing? Can I just turn off GRUB since there is only 1 OS on HDD/device sda?

Thanks for any and all help :<)

I bet it would be of interest to look at the file that grub parses to boot ->
```

cat /boot/grub/grub.cfg

```

There does exist the tools to look at where grub is installed, and what grub expects.

[INDENT][INDENT]who, what, where, when and why
[INDENT][INDENT]knowledge is power
[/INDENT][/INDENT][/INDENT][/INDENT]

---

### Post by yancek on 2014-10-25
Are you saying you get this message even though you only have one hard drive?  If you have another hard drive, did it have Ubuntu previously and was it attached when you installed Lubuntu?  In GParted it will show additional drives in the drop down in the upper right of the window.  Not sure what your situation is.

---

### Post by ajgreeny on 2014-10-25
Let's see the output of **sudo fdisk -l** which will tell us more about your disk(s) and partitions

---

### Post by mayagrafix on 2014-10-26
> **yancek said:**
> Are you saying you get this message even though you only have one hard drive?  **If you have another hard drive, did it have Ubuntu previously and was it attached when you installed Lubuntu?**  In GParted it will show additional drives in the drop down in the upper right of the window.  Not sure what your situation is.

The laptop only has 1 hard drive but for installation I attached the laptop HDD to another PC via USB. You are right, this is probably the cause of the GRUB problem. 

Gparted only shows 1 hard drive (sda1, sda2, sda5)

When I use the CAT command on /boot/grub/grub.cfg, it shows entries for Lubuntu and  Ubuntu 14.04 LTS on sdb1.

Fdisk -l only shows sda1,sda2 and sda5.

Is it safe to edit the grub.cfg? to eliminate references to sdb1 OS?

---

### Post by yancek on 2014-10-26
If you had it attached to another machine during the install that would account for it.  You should be able to remove those entries which were from the other computer now by simply running:  sudo update-grub as that will only find kernels on the current system and update the grub.cfg file.

---

### Post by oldos2er on 2014-10-26
Moved to General Help.

---

### Post by mayagrafix on 2014-10-26
> **yancek said:**
> If you had it attached to another machine during the install that would account for it.  You should be able to remove those entries which were from the other computer now by simply running:  **sudo update-grub** as that will only find kernels on the current system and update the grub.cfg file.

Yes, this solved the problem. THANKS!

---

