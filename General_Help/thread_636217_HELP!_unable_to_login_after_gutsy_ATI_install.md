---
title: "HELP! unable to login after gutsy ATI install"
date: 2007-12-09
forum: General Help
---

### Post by kishorebudha on 2007-12-09
I installed the ATI drivers (my computer Inspiron 6000 Intel Centrino 1.73mhz with ATI Mobility Radeon x300 / 128MB dedicated Memory) using the manual install instructions here: [http://wiki.cchtml.com/index.php/Ubuntu_Gutsy_Installation_Guide](http://wiki.cchtml.com/index.php/Ubuntu_Gutsy_Installation_Guide)

After following all the instructions to a T I rebooted the computer. After entering the login credentials, the computer accepts them and after a few seconds takes me back to the login screen. I logged in with Failsafe Gnome and reset xorg using the following commands.

sudo dpkg-reconfigure -phigh xserver-xorg

Did not make a difference. I spent the entire weekend customising Ubuntu to reinstall it again. Any help would be appreciated.

---

### Post by uidb4056 on 2007-12-09
May be something is wrong with the install of your ATI Drivers, the easy way to go ahead is when you get the Failsafe prompt run

dpkg-reconfigure xserver-xorg and choose a standar vga driver, when finish and after reboot you will be able to login at least with standard resolution and from there check for the right install of your drivers.

---

### Post by kishorebudha on 2007-12-09
Thanks for the response. I tried that as well. Finally had to reinstall Ubuntu.

---

