---
title: "New Graphics Card"
date: 2007-06-23
forum: General Help
---

### Post by wilialm on 2007-06-23
I have a dual boot running Ubuntu and Vista on two sata drives and it has always worked fine until i went from useing shared graphics to installing a stand alone graphics card ( Nvidia 8500GT ) now i cannot boot into Ubuntu but i can boot into Vista. When trying to boot into Ubuntu i get has far has screen where Ubuntu loads up then where it should go to the login screen, this is where i get the Black screen.I have tried useing the Live CD and it works fine. Is there a way of booting into Ubuntu without doing a reinstall.

---

### Post by confused57 on 2007-06-23
> **wilialm said:**
> I have a dual boot running Ubuntu and Vista on two sata drives and it has always worked fine until i went from useing shared graphics to installing a stand alone graphics card ( Nvidia 8500GT ) now i cannot boot into Ubuntu but i can boot into Vista. When trying to boot into Ubuntu i get has far has screen where Ubuntu loads up then where it should go to the login screen, this is where i get the Black screen.I have tried useing the Live CD and it works fine. Is there a way of booting into Ubuntu without doing a reinstall.
You might want to boot the live cd and check the /etc/X11/xorg.conf settings for your graphics card...

Can you boot into recovery mode in your installed Ubuntu?  If you can, you might want to run:
```
dpkg-reconfigure xserver-xorg
```

or manually check the settings in your xorg.conf:
```
nano /etc/X11/xorg.conf
```

You might want to try "nv" or "vesa" video drivers to get to a desktop, then you can install Nvidia drivers.

---

### Post by CREEPING DEATH on 2007-06-23
Forget recovery mode.  Bot into Ubuntu until X fails, then press CTRL+ALT+F1.  This will take you to a terminal.  Log in using your user name and password.  Then
```
sudo dpkg-reconfigure xserver-xorg
```
Follow the instructions, it usually defaults to the correct selection.  After it's complete, do
```
startx
```
It should go directly to your desktop.  If it fails, try the command again, there's a setting that's wrong.  If it works, CTRL+ALT+F1 again to return to the terminal.
```
sudo init 6
```
will reboot the system, it should reboot in a normal fashion.
ETA:  the "vesa" drivers are fairly failure-proof, but low performing.  For the best 3D video you're going to have to install the NVidia drivers, and I've been told in another thread you have to install them from NVidia (rather than the ones in the repos) for your card.

CD

---

### Post by wilialm on 2007-06-26
Thankyou for your help i did what you said and it got me back to the desktop, but when i started my computer the next day i had to go through the same proccess again because it did not save the setting. I fix my problem by useing a program called ENVY which installed the latest nvidia drivers for my graphics card 8500GT and everything works fine.

---

