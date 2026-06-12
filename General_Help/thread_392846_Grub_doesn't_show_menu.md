---
title: "Grub doesn't show menu"
date: 2007-03-25
forum: General Help
---

### Post by amdalex on 2007-03-25
Right now I have a dual boot with ubuntu edgy and windows 98. When I turn on my computer you have to press the escape key to get to the grub menu. Also the timeout is only 5 seconds. Could you guys to me how to make the grub menu automatically and how to make the timeout longer?:confused:

---

### Post by taurus on 2007-03-25
Open a terminal and edit /boot/grub/menu.lst

Applications -> Accessories -> Terminal
```
gksudo gedit /boot/grub/menu.lst
```
Then, change the **timeout** to whatever seconds you want and put a # in front of **hidemenu** so it would show the menu when you turn your machine on.

Save it and reboot.

---

### Post by amdalex on 2007-03-25
Thanks it worked.:biggrin:

---

### Post by the.dark.lord on 2007-03-25
> **taurus said:**
> Open a terminal and edit /boot/grub/menu.lst

Applications -> Accessories -> Terminal
```
gksudo gedit /boot/grub/menu.lst
```
Then, change the **timeout** to whatever seconds you want and put a # in front of **hidemenu** so it would show the menu when you turn your machine on.

Save it and reboot.

Hey people, I got a similar kind of trouble. I wiped out OS X and installed Ubuntu on an iMac, everything went fine with the installation. When I reboot, GRUB shows 

"GRUB loading, please wait...."

forever.

Please help.

---

### Post by bulldog on 2007-03-25
Try reinstalling GRUB with the live cd.
If you have only one hdd it's a piece of cake,if you have more then one,install it on your first boot disk.
Boot into the live Ubuntu cd. 
When you get to the desktop open a terminal and enter. 
```
sudo grub
```
This will get you a "grub>" prompt 
```
find /boot/grub/stage1
```
This will return a location.Use that location in the next line 
```
root (hd?,?)
```
Next enter the command to install grub to the mbr
```
setup (hd0)
```
Exit the grub shell
```
quit
```

---

### Post by the.dark.lord on 2007-03-25
bulldog, Thanks a lot for replying. I tried out what you said, and sadly it is still the same old story. And, I have only one HD. 
Disk /dev/sda: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       30032   241232008+  83  Linux
/dev/sda2           30033       30401     2963992+   5  Extended
/dev/sda5           30033       30401     2963961   82  Linux swap / Solaris

What should I do now?

---

