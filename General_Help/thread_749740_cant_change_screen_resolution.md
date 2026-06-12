---
title: "cant change screen resolution"
date: 2008-04-08
forum: General Help
---

### Post by sm4n666 on 2008-04-08
Version 7.10 32 bit
Nvidia fx 5500 256mb ddr pci slot
screen resolution 1360x768 (its a vizio)

Problem:
    i cant get past the default screen resolution 800x600.....i have multiple computers with ubuntu and i cant get it to work on my friends desktop.  i have tried editing xorg.conf file many times......tried to reset xserver and that doesnt work......i have used envy to install nvidia drivers and restricted drivers to install it.......btw it is enabled and in use....i might just be doing one of these wrong but does anyone have any suggestions for me

---

### Post by sm4n666 on 2008-04-08
also when i go to applications>system tools>Nvidia    it says that "you do not appear to be using the NVIDIA X driver.  Please edit your X configuration file (just run "nvidia-xconfig" as root), and restart the X server."  I did this and it still gives me the message (to restart it you push ctrl+alt+backspace right?

---

### Post by sm4n666 on 2008-04-09
update:  i was finally able to get the nvidia x driver....(installed 96.XXX drivers instead of new one).

---

### Post by sm4n666 on 2008-04-09
bump

---

### Post by overdrank on 2008-04-09
> **sm4n666 said:**
> update:  i was finally able to get the nvidia x driver....(installed 96.XXX drivers instead of new one).

Hi and you have the nvidia driver now in the xorg and have you tried to change the resolution with nvidia-settings? Use the command ```
gksudo nvidia-settings
```

---

### Post by sm4n666 on 2008-04-10
after i installed the 96.xxx drivers i need to enable it in restricted drivers.........then it doesnt work again........is there any way that i can keep the old drivers and enable it?

---

### Post by sm4n666 on 2008-04-10
> **overdrank said:**
> Hi and you have the nvidia driver now in the xorg and have you tried to change the resolution with nvidia-settings? Use the command ```
gksudo nvidia-settings
```

it will only let me go up to 1268x768 (with the 96.xxx drivers)

---

### Post by clarknova on 2008-04-10
It sounds like maybe your monitor hasn't been detected properly. If you have succeeded in using the nvidia driver, use **System->Administration->Screens and Graphics** to select your monitor. The Detect button often works. If not, you may have to manually enter your V and H refresh rates, which you will need to know (usually in the manual or on the manufacturer's web site).

db

---

### Post by sacredchao on 2008-04-10
I had the same problem this morning - when I booted, it was at 800x600, and nothing would happen when I tried to change resolutions from System-Preferences-Resolution. I then went to System-Admin-Screens & Graphics, and changed the resolution there, and now everything is fine. Not really sure why though, but it worked for me.

---

### Post by sm4n666 on 2008-04-10
as stated before it is a vizio tv...not monitor....it does not auto detect...i put it as generic 1368x768 monitor but the max resolution it gives me in either place is 1280x768

---

### Post by clarknova on 2008-04-10
If you find the Vertical and Horizontal refresh rates for your tv and enter them manually I think you will be in business.

db

---

