---
title: "Would like grub menu to show on boot so I can choose which os to boot"
date: 2018-01-02
forum: General Help
---

### Post by stoudy on 2018-01-02
I'm new to Ubuntu and having been trying to setup a dual boot system.  I have my BIOS set to boot my Ubuntu HDD first.  At one point, I was getting a grub menu that let me choose which OS to boot.  I didn't have to do anything special.  I disconnected my Windows drive, installed Ubuntu on a new drive, then reconnected the Windows drive.  But, I was having Nvidia and wifi driver issues and had to reinstall Ubuntu several times... because I'm a noob lol.  Now the grub menu is not displaying.  Both OSs work if I pull up the BIOS boot menu.  I'm sure this is an easy fix, but one thing I learned with messing around with my driver issues is that someone else's solution in a post may not be the solution for you and may actually hose your system up.  SO... please humble me and reply with a solution or a command you would like to see the output of lol! Thank you in advance!

---

### Post by yancek on 2018-01-02
After re-installing Ubuntu, did you run:  sudo update-grub from a terminal after attaching the windows drive?
Which release of windows are you using and which release of Ubuntu?  If you have windows 8 or 10, it is likely a UEFI/GPT install so you would need to install Ubuntu UEFI/GPT also.

---

### Post by Impavidus on 2018-01-02
When you install Ubuntu and the installer detects Windows, it should automatically configure grub to show the menu. But when you disconnect the Windows drive, it doesn't. Check the settings for grub:```
sudo nano /etc/default/grub
```(Or use your favourite text editor; with a graphical text editor use sudo -H)
Make sure the GRUB_TIMEOUT is set to some positive value. It's the duration in seconds the menu will be shown, about 5 should be fine. Then run```
sudo update-grub
```to apply the settings. update-grub will provide some output showing whether it detected Windows.

It could also be that your Windows can't be properly detected, which may happen because of the Windows option fastboot. It should be disabled to dual boot Ubuntu and Windows, but Windows updates may automatically enable it. If so, disable and run sudo update-grub.

---

### Post by stoudy on 2018-01-02
Running sudo update-grub worked!  I knew it had to be something really easy.  I ran that and it detected Win 7.  When I rebooted, the grub menu appeared automagically.

---

### Post by yancek on 2018-01-02
When you installed Ubuntu with only the Ubuntu drive attached, you had only one known operating system.  In that case, you won't see a boot menu because there is no point as there is only one option, in your case Ubuntu so you had to let Grub find the other OS once you attached the second drive.

---

### Post by stoudy on 2018-01-04
Thanks again for the help!  Am I supposed to mark this thread solved somehow?

---

### Post by QIII on 2018-01-04
Click "Thread Tools" in the menu bar just above your first post and then select "Mark this thread as solved" in the drop-down.

Cheers!

---

