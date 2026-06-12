---
title: "login to gnome then get taken back to login screen"
date: 2008-06-24
forum: General Help
---

### Post by freakydeeky on 2008-06-24
Just installed today and have no idea how to get around this problem. I can run the failsafe gnome and failsafe terminal but couldnt find anything there to fix my problem.

---

### Post by spiderbatdad on 2008-06-24
possibly...login to failsafe gnome. Open a terminal and run:```
sudo reconfigure-gdm
```

---

### Post by freakydeeky on 2008-06-24
I put it in the failssafe terminal and got command not found.


> **CaKiwi said:**
> I stumbled onto a solution to this problem. I went to System->Administration->Hardware drivers and installed the proprietary driver for my ATI Radeon XPRESS 200 video card. I can now login using the Gnome session but I would really prefer to use an open driver. Does anyone know how I can accomplish this?

I found this in another topic and that seems to be the same video card im running. I dont see how to install the driver though. I also cannot run a .exe file I transfered to my computer running ubuntu under the failsafe gnome.

---

### Post by freakydeeky on 2008-06-24
I opened a terminal in the failsafe gnome and input that command but it said command not found. I just type exactly that right when I open it?

---

### Post by bodhi.zazen on 2008-06-24
.exe files are windows binaries and aer unlikely to run in Ubuntu.

What videocard are you using ? How did you install ?

---

### Post by spiderbatdad on 2008-06-24
sorry about that. Please try ```
sudo gdmsetup
```

---

### Post by CaKiwi on 2008-06-24
What happens when you click on

System->Administration->Hardware drivers

in failsafe Gnome? When I did it, I got a message telling me I needed to install a proprietary driver for my video card and it guided me through the installation

---

### Post by freakydeeky on 2008-06-24
ati radeon express 200

I downloaded the bootable .iso from the ubuntu page and just popped it in my computer

---

### Post by freakydeeky on 2008-06-24
sudo gmdsetup comes up as cannot be found

When I go to the hardware drivers it says no proprietary drivers are running on this computer and it only lists ati fire gl as enabled in the drivers window

---

### Post by freakydeeky on 2008-06-24
ran sudo gdmsetup and got to the the login config screen but didnt see any options that mightve fixed my problem

---

### Post by spiderbatdad on 2008-06-24
> **freakydeeky said:**
> sudo gmdsetup comes up as cannot be found

When I go to the hardware drivers it says no proprietary drivers are running on this computer and it only lists ati fire gl as enabled in the drivers window

You have a typo...gdmsetup not gmdsetup :)  Not sure it will fix your problem, but worth a shot.

---

### Post by freakydeeky on 2008-06-24
yeah my apoligies I can get to that screen but dont understand if any of the options will fix my problem

---

### Post by spiderbatdad on 2008-06-24
another possibility is ```
sudo dpkg-reconfigure -phigh xserver-xorg
```

---

### Post by CaKiwi on 2008-06-24
You have the same video card and the same problem that I had. I forget the exact sequence of events I used to fix it but I went to System->Administration=>Hardware Drivers and fooled around until it asked me to install the proprietary ATI driver.

---

### Post by freakydeeky on 2008-06-24
I dont have any options there though and no internet access because i dont have the driver for my wireless thing

---

### Post by freakydeeky on 2008-06-24
> **spiderbatdad said:**
> another possibility is ```
sudo dpkg-reconfigure -phigh xserver-xorg
```

:/ nothing

---

### Post by freakydeeky on 2008-06-25
well im running in failsafe gnome now with my wireless bridge I use for my xbox.I got most things running alright but I installed a windows driver for my other wireless bridge that id like to use for this computer but every time i plug the bridge in the computer freezes.

---

### Post by freakydeeky on 2008-06-25
Im using the windows wireless driver program and install the driver from my wusb54g.inf file but when I plug it in the computer freezes

---

