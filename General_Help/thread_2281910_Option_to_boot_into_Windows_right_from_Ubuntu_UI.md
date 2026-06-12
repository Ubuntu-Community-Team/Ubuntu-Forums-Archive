---
title: "Option to boot into Windows right from Ubuntu UI?"
date: 2015-06-10
forum: General Help
---

### Post by keenPenguin on 2015-06-10
Hey guys, 

many moons ago on SuSE with KDE, I remember there was an option in the UI to boot to Windows. So when you had a dual boot setup, you were able to click on that button and magically the boot loader menue would be skipped and there you were in Windows. I really miss such a feature. When I am working on Ubuntu and I suddenly need to do something on Windows, I have to click restart and then wait for the boot menu to select Windows, because Linux is the default boot option. Can I install a "boot to Windows" feature in Ubuntu?

---

### Post by SeijiSensei on 2015-06-10
A better option might be [VirtualBox]("https://www.virtualbox.org/").  Then you can have a Windows machine immediately available without rebooting.

---

### Post by CantankRus on 2015-06-11
The command ```
grub-reboot
```
allows you to "Set the default boot menu entry for GRUB, for the next boot only."

See **man grub-reboot**

In 14.04 I can use this command to list my grub entries....
```
grep menuentry /boot/grub/grub.cfg | grep "^menuentry" | sed -e 's/.*Memory test.*//g' -e "s/menuentry '//g" -e 's/ --class.*//g' -e "s/'//g" -e '/^$/d'
```

eg
```
**[COLOR="#008000"]glen@Trusty:~$[/COLOR] grep menuentry /boot/grub/grub.cfg | grep "^menuentry" | sed -e 's/.*Memory test.*//g' -e "s/menuentry '//g" -e 's/ --class.*//g' -e "s/'//g" -e '/^$/d'**
Ubuntu
[COLOR="#0000CD"]Windows NT/2000/XP (loader) (on /dev/sda1)[/COLOR]
Ubuntu 15.04 (15.04) (on /dev/sdb1)
elementary OS Luna (0.2) (on /dev/sdc1)
Ubuntu 14.04.2 LTS (14.04) (on /dev/sdc5)
```

If this command does not work for you just look in **/boot/grub/grub.cfg** for your actual windows boot entry.

From my above output I can then run
```
pkexec grub-reboot "[COLOR="#0000CD"]Windows NT/2000/XP (loader) (on /dev/sda1)[/COLOR]" && gnome-session-quit --reboot
```
If you want to be able to run **grub-reboot** without authenticating Admin, run...
```
sudo chmod +s /usr/bin/grub-editenv
```
You can then drop the "pkexec" from the command.

I create a unity launcher to run the command or you could create a bash alias.
[ATTACH=CONFIG]262519[/ATTACH]
This is my script that the unity launcher runs....
**Reboot_to_Windows** (aka "the coffee break")
```
#!/bin/bash

## grub-reboot sets the default boot entry for GRUB, for the next boot only
## To enable grub-reboot to be edited by any user run
## sudo chmod +s /usr/bin/grub-editenv

## To find the grub menu entry you want run
## grep menuentry /boot/grub/grub.cfg | grep "^menuentry" | sed -e 's/.*Memory test.*//g' -e "s/menuentry '//g" -e 's/ --class.*//g' -e "s/'//g" -e '/^$/d'

# my windows grub menu item
grubentry="[COLOR="#0000CD"]Windows NT/2000/XP (loader) (on /dev/sda1)[/COLOR]"


grub-reboot "$grubentry"  # preface with pkexec if you didn't run the chmod command  
gnome-session-quit --reboot
```
P.S: I also lower both the windows loader timeout and the GRUB_TIMEOUT to 3secs.

I don't know your level of expertise so you may want to look at [**_[COLOR="#B22222"]unity-reboot[/COLOR]_**]("http://www.webupd8.org/2013/01/unity-reboot-launcher-to-quickly-reboot.html") which will do most of this for you in unity.

---

### Post by Bucky Ball on 2015-06-11
*Thread moved to **General Help**.*

---

