---
title: "Question regarding fixing grub2"
date: 2013-06-20
forum: General Help
---

### Post by zemega on 2013-06-20
I have Ubuntu 13.04 and Windows 7. Then I installed OpenSuse 12.3 . After that using external USB, I boot into Ubuntu 13.04, trying to fix so that the laptop use Ubuntu grub. After going through several tutorial and did not manage to, I just try sudo apt-get install grub, then sudo apt-get install grub2. Its working as before now. Now, was this method advisable? Is there any bad side to it?  Because 2 line commands just beat a few page of tutorial of fixing grub/grub2. I'm certainly new to this, so please enlighten me on anything that you think I should know.

---

### Post by dino99 on 2013-06-20
grub: the oldish legacy package (with its menu.list): no more used, deprecated by grub-pc (aka grub2)

you should purge "grub" and its menu.list, to stop grub2 been disturbed.

to install grub2 : sudo grub-install /dev/sda
to reconfigure: sudo dpkg-reconfigure grub-pc

more info with the link below :)

---

### Post by grahammechanical on 2013-06-20
The situation is this: When a distribution uses Grub as the boot loader then the last distribution installed will put its version of Grub into the MBR of the hard disk and that distribution will be at the top of the menu. If you want Ubuntu to be at the top of the menu then you must put the Ubunty Grub back into the MBR. We do this but loading into Ubuntu and running

```
sudo update-grub
```
```
sudo grub-install /dev/sda
```

Assuming that there is only one hard disk (sda) and you want Grub in the MBR of sda and not another hard disk (sdb, sdc etc.)

The first command updates the grub configuration file on the Ubuntu partition and detects all the OS it can find. The second command installs Grub into the MBR and it will look for its configuration file on the Ubuntu partition.

I have several installs of Ubuntu (different versions) and I use this method to keep one special Ubuntu in charge of the Grub menu. I have installed the selection of grub2-splashimages in the software centre. They get put into /usr/share/images/grub. I select one and copy it into /boot/grub and then I run those two commands and that gives me a background image for the grub menu. When that background image changes, then I know that some other installation has taken control of the Grub menu in the MBR.

You will need administrator privileges to copy an image into /boot/grub. Run

```
gksudo nautilus
```

and then you will get a file manager with administrator privileges.

Regards.

---

### Post by zemega on 2013-06-20
I see. So that;s how you do it properly.

---

