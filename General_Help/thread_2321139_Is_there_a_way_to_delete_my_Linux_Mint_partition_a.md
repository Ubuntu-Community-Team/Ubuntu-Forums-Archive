---
title: "Is there a way to delete my Linux Mint partition and expand my Ubuntu partition?"
date: 2016-04-20
forum: General Help
---

### Post by Alexei_Solonari on 2016-04-20
I decided to try Linux Mint.
But I didn't like it.

Luckily I didn’t wipe my data and I still have an Ubuntu partition. 
Can I delete my LM partition and expand my Ubuntu one?

---

### Post by oldfred on 2016-04-20
Usually last install is the version of grub in control of booting with MBR/BIOS systems.
You must install Ubuntu's grub to MBR, or you will get the Mint grub in MBR looking for Mint that does not exist and grub> error. Then you need to have Ubuntu live installer to repair grub.

Boot into Ubuntu and reinstall grub from that. Best to always have a working live installer just in case.

 #reinstall from working (not liveCD/DVD/USB) system - first find Ubuntu drive (example is drive sdb but use your drive not partitions):
sudo parted -l
#if it's "/dev/sdb"  then just run:
sudo grub-install /dev/sdb
#If that returns any errors run:
sudo grub-install --recheck /dev/sdb
sudo update-grub

---

### Post by Alexei_Solonari on 2016-04-20
so i type that in terminal?

and sda4 is LM
sda2 is Ubuntu

---

### Post by nerdtron on 2016-04-20
Yes, you'll do that on while you're on Live environment (booting ubuntu from USB).

Also, we're not sure yet on how you're partitions are setup. You can necessarily "expand" the Ubuntu after deleting the Mint partition. So it would be better if you also post here your drive layout. Either a screenshot from the Disks Utility of from the command line:

```
sudo parted -l
lsblk

```

---

### Post by magus3 on 2016-04-20
You could install gparted ([http://gparted.org/](http://gparted.org/)) on Mint. There is a gui which should be more intuitive if you're a beginner.

---

### Post by Cavsfan on 2016-04-21
> **Alexei_Solonari said:**
> so i type that in terminal?

and sda4 is LM
sda2 is Ubuntu

You just need to boot into Ubuntu and enter:
```
sudo grub-install /dev/sda
```

If that returns any errors, Like oldfred said run:
```
sudo grub-install --recheck /dev/sda
```
Then:
```
sudo update-grub
```

Then install Gparted
```
sudo apt-get update && sudo apt-get install gparted
```

Like          nerdtron said you should post the contents of either 
```
lsblk
``` or ```
sudo blkid
```
Wrap the output in CODE tags so it's easier to read.

Because if **sda3** is your swap, you will have to do this in a live session.
If it's not swap and is a partition you want to keep it will be more difficult.

But show us the output first.

Regards

---

