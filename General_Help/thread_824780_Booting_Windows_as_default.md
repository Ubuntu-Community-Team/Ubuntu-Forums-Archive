---
title: "Booting Windows as default?"
date: 2008-06-10
forum: General Help
---

### Post by davideotape on 2008-06-10
Hi guys

I have a problem. I want to install Ubuntu on my home PC that already has windows vista installed on it. I have the live CD, know how to install it and have done it on another computer by using the auto partitioner so I had XP and Ubuntu. However, when I installed it on the other computer I noticed the Ubuntu OS was default in the menu that pops up shortly after booting, and if no action is taken the computer automatically boots into Ubuntu. I was wondering if there was a way to make Windows the default (ie. top of the list) when booting. 

All help appreciated! :)

---

### Post by Pjotr123 on 2008-06-10
Check this simple how-to:
[http://ubuntutip.googlepages.com/tipsandtweaks](http://ubuntutip.googlepages.com/tipsandtweaks)
(number 1 )

---

### Post by crossedout on 2008-06-10
> I was wondering if there was a way to make Windows the default

Sure you can.  Login to Ubuntu, jump to terminal and enter:
```
sudo gedit /boot/grub/menu.lst
```

Look for the following section:
```
## default num
# Set the default entry to the entry number NUM. Numbering starts from 0, and
# the entry number 0 is the default if the command is not used.
#
# You can specify 'saved' instead of a number. In this case, the default entry
# is the entry saved with the command 'savedefault'.
# WARNING: If you are using dmraid do not change this entry to 'saved' or your
# array will desync and will not let you boot your system.
default 0
```

Change the 'default' 0' to match the Windows boot section.  It will probably be '4' but you'll need to match that to your needs.

-Xout

---

### Post by MariusSilverwolf on 2008-06-10
Try this:

```
sudo gedit /boot/grub/menu.lst
```

Scroll down to the bottom of the file, and count down from the first Title entry (e.g Title    Ubuntu 8.04, kernel 2.6.24-18 generic) until you find the entry for Windows.  Numbering starts at 0, so if Windows is the 4th down, that would be entry 3.

Scroll back to the top of the file.  Look for the "default num" section.  Change the default number to that which matches the number for the Windows entry (3 in our example).

Save, exit, reboot to test.

---

### Post by drs305 on 2008-06-10
You can make windows the default through StartupManager. System, Admin, Startup-Manager. If you don't see it, install it with:
```
sudo apt-get startupmanager
```

I strongly recommend making changes to the grub menu via startup-manager. It protects you from screwing up the menu.lst. For many of the display options you have control over, see:
[HOWTO: Grub Menu Kernel Display Options]("http://ubuntuforums.org/showthread.php?t=818177")

---

