---
title: "Some issues with Ubuntu"
date: 2005-10-17
forum: General Help
---

### Post by UbuntuUbuntu7 on 2005-10-17
Hello, i recently started to use Ubuntu and it&#347; great, but i have som issues and questions if you can quickly answer it or link to a guide somewhere it would be great.

The keyboard i use. I can t get some of the keys to work. Im thinking about the ones where the numbers are and you press "shift". These dont come up. Like the " @" sign.

The mouse. I have buttons on the side, with which i can go back and forward in the browser without to have to use the arrows up to the left. These dont work. What to do?

Desktop background. There is only the brown desktop background. How can i get others? Im not thinking about themes here, because there you can choose as i have seen many variants. But im thinking about the pure brown desktop. In System-Preferences-DesktopBackground(i think it is, i dont use english Ubuntu) there is just three brown choices. I want another colour. How? 

The graphic card. I used this guide: [http://ubuntuguide.org/#installnvidiadriver](http://ubuntuguide.org/#installnvidiadriver)
I have a PalitDaytona geforce4 ti4200 245 agp8x. Its really a nvidia gpu. Did i do right? Did i get the newest ones, or is there newer updates?

Tv-card. I have a WintvGo2 haupauge. Someone know a guide on how to install it?

Services. Under: System-Administration-Services... is this the only services that are running? Its not much actually, is there another services tab to look at?

Ip tables. I know about sudo iptables --list. But how do i configure it?

Thanks in advance.

---

### Post by aclaunch on 2005-10-17
Keyboard: look at System->Preferences->Keyboard (is yours configured as US, 104,etc?-these are standard keyboards)

Mouse: don't remember but google "Linux multi button mouse"; there are lots of how-tos.

Background: right-click on the desktop->change background. You can add almost any graphic in Firefox. Right-click the image and choose  "set as wallpaper".

Services: these are only some of the services running. You can get a better idea from running "ps aux" in a terminal. This gives a list of running processes. 

iptables: you can configure manually but a firewall like Firestarter or Guarddog is much easier. Firestarter is available via apt/synaptic and I assume Guarddog is also (Firestarter is a GTK/Gnome app, Guarddog is QT/KDE).

Good Luck,
Alan

---

### Post by UbuntuUbuntu7 on 2005-10-17
[QUOTE=aclaunch]Keyboard: look at System->Preferences->Keyboard (is yours configured as US, 104,etc?-these are standard keyboards)

Mouse: don't remember but google "Linux multi button mouse"; there are lots of how-tos.

Background: right-click on the desktop->change background. You can add almost any graphic in Firefox. Right-click the image and choose  "set as wallpaper".

Services: these are only some of the services running. You can get a better idea from running "ps aux" in a terminal. This gives a list of running processes. 

iptables: you can configure manually but a firewall like Firestarter or Guarddog is much easier. Firestarter is available via apt/synaptic and I assume Guarddog is also (Firestarter is a GTK/Gnome app, Guarddog is QT/KDE).

Good Luck,
Alan[/QUOTE]

Thank you very much for your response :D . I will not care about the buttons on the mouse for now...
The keyboard, though. Its swedish, and it says that in "layout". And on model it says: "Allm&#228;n("Generic" in english?) 105-tangenters (internationell) PC".  Maybe it'something under "layout alternative" that has to do with it. The changes take effect immediatley, right? So i dont have to reboot....?

Another one said it could have to do with the config in: "/etc/X11/xorg.conf" Anyone with swedish keyboard that fixed this?

Another thing. My internet connection is broken after reboot. I have cable modem. 

Under System-Administration-Network, there is two devices where it says: 1. "Ethernet, interface eth0 is active." This seems to be my network card in the computer. 2. "Modemconnection, interface pppo is not configurated." 

Can this have anything to do with that my connection is broken after reboot? If i choose "enable this connection" and then "detect automaticly"(the modem port) it says "could not automaticly detect the modem unit." Could this be a worry? I mean... i can get out on the internet, but it&#347; just that it&#347; broken after reboot..... :???: If someone know, please make some input. ;) 

Thanks again, Alan.

---

### Post by aclaunch on 2005-10-17
As far as I know, the "keyboard preferences" dialog is just a graphical interface to the actual keyboard settings in /etc/X11/xorg.conf. 

Under System->Administration->Networking: are all the values entered and correct? For whether you get your IP by DHCP or a fixed IP, DNS servers, etc. Again this is just a graphical interface to several configuration files in /etc and when you save the configuration, it gets written to the appropriate file in /etc and applied at reboot.

You don't need to configure the modem unless you want to use the modem; this is a separate device from your cable connection. But make sure that your cable interface, probably eth0, is active.

Good Luck,
Alan

---

### Post by oscarh on 2005-10-17
afaik keyboard layouts are very broken in breezy?!?!
however, if you only use one layout that would not be a ploblem.

in xorg.conf it should look like this:
```
Section "InputDevice"
        Identifier      "Generic Keyboard"
        Driver          "kbd"
        Option          "CoreKeyboard"
        Option          "XkbRules"      "xorg"
        Option          "XkbModel"      "pc105"
        Option          "XkbLayout"     "se"
        Option          "XkbVariant"    "nodeadkeys" #only if you want to otherwise, removi this line
EndSection
```

---

### Post by Biased turkey on 2005-10-17
I am having a keyboard problem too with the French Canadian keyboard and breezy.
I used the GUI to modify the keyboard and got an error message, then edited my xorg.conf  specifying the "ca_enhanced" keyboard but my keyboard is still not configured properly.
My 2nd rig with Ubuntu 5.04 doesn't show that keyboard problem.
Bur hey, we shouldn't complain because we are pioneers exploring new teritories.

---

### Post by UbuntuUbuntu7 on 2005-10-18
Ok... i fixed the keyboard issue for enyone allso having the same problem. Instead of ctrl+alt+2 that i have ALWAYS used, it`s now alt gr+2 to get the "@" ;)

---

### Post by Cyhatch on 2005-12-02
On the fact that modifying [FONT="Courier New"]xorg.conf[/FONT] doesn't solve the problems:

I've read somewhere that [FONT="Courier New"]xkb[/FONT] and Gnome have different settings, or something. [FONT="Courier New"]/etc/X11/xorg.conf[/FONT] and [FONT="Courier New"]~/.gconf/[/FONT] respectively.

So, AMAIU, Gnome takes the X11 configuration and "modifies" it, right?

---

