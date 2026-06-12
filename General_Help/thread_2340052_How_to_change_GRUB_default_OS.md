---
title: "How to change GRUB default OS?"
date: 2016-10-15
forum: General Help
---

### Post by Kpenguin on 2016-10-15
Hi,
I recently did a fresh install of Ubuntu 16.04. I'd like to change the default OS on GRUB. Has this changed in 16.04? I looked at the community help wiki and it involved editing menu.lst. I entered this command:
```
gksudo gedit /boot/grub/menu.lst
```
But it said no such file or directory. Where can I find this in 16.04?

Thanks!
Kpenguin

Also, has the location where GRUB themes are installed change as well?

---

### Post by dord2 on 2016-10-15
There is no menu.lst in grub2, only grub.cfg.
To edit grub i use the grub customizer [http://ubuntuhandbook.org/index.php/2016/04/install-grub-customizer-ubuntu-16-04-lts/](http://ubuntuhandbook.org/index.php/2016/04/install-grub-customizer-ubuntu-16-04-lts/)

---

### Post by Kpenguin on 2016-10-15
Where do I find grub.cfg?

---

### Post by yancek on 2016-10-15
You need to check dates on the web sites as that one is at least 6 years old.  Grub2 which is used on Ubuntu 16.04 has a file named grub which you can edit.  If you use the gedit text editor type the following command in a terminal:

```
sudo gedit /etc/default/grub
```

That should open the file you need to edit and the line you need to change is right at the top, shown below:

> GRUB_DEFAULT=0

Look at the entries in your boot menu when booting the computer and change the number zero show to the correct number.  In this instance, Grub counts from zero so if the entry you want as default is the third entry, put the number 2 there.  After doing this you need to run:  sudo update-grub in the terminal.

---

### Post by oldfred on 2016-10-15
Manually editing with screen shots as yancek suggested:
[http://www.psychocats.net/ubuntu/bootmenu](http://www.psychocats.net/ubuntu/bootmenu)

Lots of info on customizing grub2.
       How to: Create a Customized GRUB2 Screen that is Maintenance Free.- Cavsfan
[https://help.ubuntu.com/community/MaintenanceFreeCustomGrub2Screen](https://help.ubuntu.com/community/MaintenanceFreeCustomGrub2Screen)
[https://help.ubuntu.com/community/Grub2/CustomMenus](https://help.ubuntu.com/community/Grub2/CustomMenus)
[http://ubuntuforums.org/showthread.php?t=2076205](http://ubuntuforums.org/showthread.php?t=2076205)
[https://help.ubuntu.com/community/Grub2/Displays](https://help.ubuntu.com/community/Grub2/Displays)

---

### Post by Kpenguin on 2016-10-15
Works great! Thanks!

If I wanted to install a premade GRUB theme (like [this]("https://www.gnome-look.org/p/1009236/")) where do I need to put that?

---

