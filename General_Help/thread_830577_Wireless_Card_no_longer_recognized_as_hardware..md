---
title: "Wireless Card no longer recognized as hardware."
date: 2008-06-16
forum: General Help
---

### Post by durundal on 2008-06-16
I am running xubuntu 8.04 on an HP laptop and after I added this script to be run at startup:

```
#/bin/bash
xmodmap -e "keycode  22 = BackSpace"
```

my internal wireless card is no longer recognized using the sysinfo application and the hardware driver has disappeared off the list.

This was the first script I have ever written and as you can see I did it wrong.  

What exactly have I done to my system and is there any way to fix it?

---

### Post by prince_niceguy on 2008-06-16
I do not think this would stop your wireless card... was there any kernel update recently which you did?

what is your card? if you are using ndiswrapper or something then you will have again add install the card drivers if there is a kernel update..

---

### Post by durundal on 2008-06-16
I know the card is Broadcom but I'm not sure exactly what model number it is because I never had to mess with it much.  After I installed xubuntu the operating system recognized it and I installed the drivers from the "Hardware Drivers" window.  Right now those drivers have disappeared off of the page.
  
By running the command lspci and using this application called sysinfo it seems that xubuntu can't detect the device at all. 

I also have only updated from the update manager and everything was working fine until I restarted it with that text file set to run at start up.

Edit: It also appears that my dvd drive is not recognized...

---

### Post by Zorael on 2008-06-16
Likely you did a kernel upgrade; that script should not be able to mess things up the way you're describing.

Make sure you have the modules properly package installed by entering the following in a terminal.
```
$ sudo aptitude install linux-generic
```
If it downloads and installs something, yay, save your work and restart your system. If it doesn't, try this; it's the package you want, but it's better to have it get pulled as dependency by linux-generic.
```
$ sudo aptitude install linux-ubuntu-modules-`uname -r`
```

---

### Post by durundal on 2008-06-16
For both of those it gave me the message "No packages will be installed, upgraded, or removed." along with some other stuff like "0 packages upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
Need to get 0B of archives. After unpacking 0B will be used."


I tried restarting anyways but the card is still not recognized.

Edit:  Hmm, I ran some other updates and then left my computer off for a while and somehow it's working again.  I'm not sure quite what did it :???: Oh well, thanks for your help.

---

