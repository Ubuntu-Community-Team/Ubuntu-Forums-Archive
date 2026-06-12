---
title: "Boot Graphical issues"
date: 2008-05-07
forum: General Help
---

### Post by razlken on 2008-05-07
Hi, I've installed Ubuntu Hardy on my new laptop dell insprion 1525(bought with no OS), it worked great for 1 day (even if it took me 4 hours to understand how to make wifi work). afterwards i downloaded compiz-fusion and AWN (not sure if this is the cause), after that the system doesn't boot anymore, instead after the boot loading some strange colored lines pop up, they disappear then the monitor turns black and turns on off repeatedly. Ok I'm not a complete idiot in computers so i figured it's a driver problem, so i booted in recovery mode and it booted fine (and all effects were working). i downloaded Nvidia binary x.org driver ('new' driver) from the add/remove app. but with no luck still doesn't load up and when i returned in recovery mode it won't load any effects anymore tried reactivating them but it tells me it's not possible. & AWN doesn't open at all. any idea?

so i got the doubt that i maybe don't have a nvidia card (i'm actually 90% sure) and since I'm still a noob can't figure out how to check what hardware i got.any command line that can help?

apart from that some updates continuosly fail 2 named xulrunner-1.9 & xulrunner-1.9-gnome-support. dunno if they are even important, are they?

one last question, i installed it using all the hard drive so now i got only one partition, is there a way to divide the partition in 2 (it's 160gb, making it 100 & 60) without formatting the partition and leaving the OS intact?
any help would really be appreciated...Thx in advance

---

### Post by drs305 on 2008-05-07
```
 sudo lshw -html > ~/Desktop/hardware.html 
```
will create an easy-to-read file on your desktop.

You can see it in a terminal window by just typing (but the first option is easier to read):
```
sudo lshw
```

---

### Post by razlken on 2008-05-07
well thx for the fast reply, well it seems I'm an idiot, it's not a  nvidia card but a Mobile GM965/GL960 Integrated Graphic Controller... so now I'm lost what should i do to solve the problem?

i used the " cat /etc/X11/xorg.conf" command and in the "Device" section i find written:

Identifier "Device0"
Driver "nvidia"
Vendorname "Nvidia Corporation"

did i mess it up for someting and is there a way to resolve it?

---

### Post by smartboyathome on 2008-05-07
You might have to reinstall Ubuntu. You shouldn't have to install compiz, it is already installed. I have the same graphics card and that doesn't happen.

---

### Post by razlken on 2008-05-07
i used this [website]("http:/forlong.blogage.de/article/2008/4/26/How-to-set-up-Compiz-Fusion-074") to install compiz don't know if it's right or not take a look and tell me.

---

### Post by damis648 on 2008-05-07
After installing the driver from the "Hardware Drivers" dialog, just restart and some compiz effects will be activated. To customize them, just install "compizconfig-settings-manager" and the settings will be under Preferences>Advanced Desktop Effect Settings.

PS!:if the shadows on the windows are nonexistent or pink or yellow or just not black, this is a bug in the nvidia drivers so run this command in terminal:
```
sudo ln -sf /usr/lib/nvidia/libwfb.so.xserver-xorg-core /usr/lib/xorg/modules/libwfb.so
``` and then restart.

---

### Post by razlken on 2008-05-07
well, i know i may sound stupid but, it seems that ubuntu read my graphic card as nvidia but i don't have an nvidia card, i tried uninstalling the driver but it give me an error so don't know what to do. and if i try to set the visual effects to extra it tells me "desktop effects could not be enabled" so don't think that's a compiz prob, or is it?

---

