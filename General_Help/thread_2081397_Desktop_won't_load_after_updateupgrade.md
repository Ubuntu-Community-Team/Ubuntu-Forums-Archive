---
title: "Desktop won't load after update/upgrade"
date: 2012-11-06
forum: General Help
---

### Post by SublimeHiPpOs on 2012-11-06
I'm running 12.10 (this was a clean install a few weeks ago). Two days ago (I believe) I ran apt-get update and upgrade (had done this several times before. I think think there was a kernel upgrade or something this this though. I am using Ubuntu's encryption on the OS drive, if I hit escape when I enter the encryption password I see "/scripts/local-top/cryptroot: line 1: can't open /dev/mapper/ubuntu-root: no such file", but it seems to continue to boot from there. I get to the login page where it prompts for my password, upon entering it only my background image loads, no menu bar or anything at all. I can right-click and see the basic context menu options (create new folder, organize desktop by name, change desktop backgroud) I can also ctrl+alt+t to get a terminal window, but right after entering my password I see a brief message saying that the network is disconnected (using wired Ethernet). Apparently something in the update or upgrade royally jacked things up, I'm just not sure where to go from here. Any help would be much appreciated so I don't have to start all over from scratch! Thanks!

---

### Post by SublimeHiPpOs on 2012-11-06
For what it's worth, when I got to the advanced options while booting I have Linux 3.5.0-17-generic and 3.5.0-18-generic (as well as the "recovery mode" versions of each. 17 must have been what I originally installed and 18 must have been the upgrade. Going back to 17 yielded almost the same results as 18, except for it looks like I have network access with 17.

---

### Post by josephmills on 2012-11-06
> **SublimeHiPpOs said:**
>  but it seems to continue to boot from there. I get to the login page where it prompts for my password, upon entering it only my background image loads, no menu bar or anything at all. I can right-click and see the basic context menu options (create new folder, organize desktop by name, change desktop backgroud) I can also ctrl+alt+t to get a terminal window, 

What happens when you run 
```
unity --replace 
```
 
The screen should flicker this is normal But this will replace the unity that is open and start a new one in the terminal (kinda) You will get a bunch of messages if unity loads. If not you will get segmentation fault and please post that here. 

Thanks

---

### Post by SublimeHiPpOs on 2012-11-06
I tried that and got: "The program 'unity' is currently not installed"...

I am running this system primarily as a media/file server and rarely use the UI. However none of the services seem to be running either, so I think the problem is deeper than just the UI.

Thanks for the reply!

---

### Post by P-I H on 2012-11-07
I had that problem the other day, when I updated my 12.10 installation.
The kernel was changed from 3.5.0-17 to 3.5.0-18.
I have a new Nvidia card gtx660. During the update the driver was changed from Nvidia current to Nouveau and the desktop did not start. I only got the background. However I was able to start the terminal by Ctrl+Alt+T and able to start programs.
I fixed the problem in this way
-installed linux-headers-generic
-used the command software-properties-gtk in the terminal to start software sources and use the gui to change back to the Nvidia driver.

---

### Post by elselu on 2012-11-07
> **P-I H said:**
> I had that problem the other day, when I updated my 12.10 installation.
The kernel was changed from 3.5.0-17 to 3.5.0-18.
I have a new Nvidia card gtx660. During the update the driver was changed from Nvidia current to Nouveau and the desktop did not start. I only got the background. However I was able to start the terminal by Ctrl+Alt+T and able to start programs.
I fixed the problem in this way
-installed linux-headers-generic
-used the command software-properties-gtk in the terminal to start software sources and use the gui to change back to the Nvidia driver.

Thanks!! I upgraded my setup of Ubuntu 12.10 this morning and after the restart the unity bar and everything was gone, only a blank screen. The ctrl+alt+t helped me to open terminal, then chromium and search something on the internet, everything useless until I found your post :) I have Geforce GT 440

I don't know why linux-headers were not installed, I thought they were (I installed some stuff at the beginning and it seemed to be installed)

---

### Post by SublimeHiPpOs on 2012-11-07
Installing the generic linux headers and switching the drivers (for my gpu (nVidia 7400GO mobile chip in the laptop) and for the Broadcom networking chip) did get my display looking better (now using the native resolution) and networking works with the new kernel. The services now appear to be running (or at least are now accessible by other devices on the network.) This meets most of my needs, but administration may still be a challenge as I still can't get a fully functioning desktop on the machine (but I can access the terminal and any application I can launch by command). Any other suggestions on how to get my desktop back?

Thanks again!

---

### Post by P-I H on 2012-11-08
The NVIDIA GeForce Go 7400 GPU is quite old. I am not sure, but I think your only choice in Ubuntu 12.10 is to use the vesa driver, as Nvidia's legacy driver will not work.

I do not guarantee this will work, but try to change to the vesa driver in Software Sources. In case /etc/X11/xorg.conf includes information about Nvidia, you have to delete it or rename it. In other case the vesa driver will not work. You can rename /etc/X11/xorg.conf, with the command
**sudo mv /etc/X11/xorg.conf /etc/X11/xorg.conf-old**
To check the content of /etc/X11/xorg.conf, you can use the command **nano /etc/X11/xorg.conf**

---

