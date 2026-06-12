---
title: "/etc/X11/xorg.conf"
date: 2005-10-30
forum: General Help
---

### Post by n1x0n on 2005-10-30
Hi All!
My Ubuntu Breezy Badger 5.10 Is Running "Slowly"
My friend is saying that is because i have "curvy" /etc/X11/xorg.conf configuration...
But i don't know english very well... And maybe someone can help me with it... :(
I realy like Ubuntu Breezy Badger 5.10, but i whant him to run faster... :)
Maybe someone can give me "some tutorials" about configurating /etc/X11/xorg.conf...
So, please, please help me with /etc/X11/xorg.conf :(
:rolleyes:
Thankyou & sorry for my english...

---

### Post by Dracontopes on 2005-10-30
You can configure your xorg.conf with this command (in terminal):
```
sudo dpkg-reconfigure xserver-xorg
```
It will ask you some questions that you must answer and it will create a new xorg.conf for you. Make sure you backup your old one! (the reconfigure command will back it up for you, but just to be sure :D)

What do you mean with "slow" ? Did you install your graphicsdriver correctly? (although the standard drivers are working very nice) I don't really think that tweaking xorg.conf will make things faster but who knows. 

You also might want to run ```
top
``` from a terminal and check your cpu usage...

---

### Post by n1x0n on 2005-10-30
Cpu Usage - ~1%
Ram Usage - ~100mb

No, I Didn't Install Any Drivers :(

---

### Post by Dracontopes on 2005-10-30
[quote=n1x0n]Cpu Usage - ~1%
Ram Usage - ~100mb

No, I Didn't Install Any Drivers :([/quote] 
What are your computer specifications? (CPU type/speed, RAM etc.)

If you have a nVidia graphicscard then installing the drivers are pretty easy, search the forums for a how-to.
If you have ATi, try this how-to: [**     HOW-TO: ATI fglrx driver 8.18.8**]("http://ubuntuforums.org/showthread.php?p=423589")

If you have another videocard, I think your stuck with the default drivers (which are good enough IMO), or maybe search the forums for help on that :P

Edit: Oh and maybe this will help a bit (it did here): do ```
gconf-editor
``` and look for the key named **reduced_resources** and enable it.

---

### Post by n1x0n on 2005-10-30
Is that tutorial good?

Installer
	Download Link 	File Size (MB) 	Date Posted 	Additional Info
ATI Driver Installer
	Download 	51.0 	10/26/05 	Version: 8.18.8

 
X-Windows Version
	Download Link 	File Size (MB) 	Date Posted 	Additional Info
XFree86 4.1
	Download 	11.5 	10/26/05 	Version: 8.18.8
XFree86 4.2
	Download 	11.5 	10/26/05 	Version: 8.18.8
XFree86 4.3
	Download 	11.5 	10/26/05 	Version: 8.18.8
X.Org 6.8
	Download 	11.5 	10/26/05 	Version: 8.18.8


If i will download driver from web site:
Which i need to install ATI VIDEO DRIVER?
I have ATI RADEON 9600 PRO.

BTW.
I Hawe:
AMD ATHLON 2000+ XP
512MB of RAM
ATI RADEON 9600 PRO
Smth else? ;)

---

### Post by Dracontopes on 2005-10-30
That it the most up-to-date how-to I think and it worked for me. (thanks mlomker :P)
Your specs are OK for Ubuntu, should not be a problem... 

The how-to says you must download " ATI Driver Installer" from the website so grab that one! ;)

---

### Post by n1x0n on 2005-10-30
Reboot.

Installing the new driver

Download the ATI driver installer: Click here.



Mhmmm... but which driver i need?

Installer
	Download Link 	File Size (MB) 	Date Posted 	Additional Info
ATI Driver Installer
	Download 	51.0 	10/26/05 	Version: 8.18.8

 
X-Windows Version
	Download Link 	File Size (MB) 	Date Posted 	Additional Info
XFree86 4.1
	Download 	11.5 	10/26/05 	Version: 8.18.8
XFree86 4.2
	Download 	11.5 	10/26/05 	Version: 8.18.8
XFree86 4.3
	Download 	11.5 	10/26/05 	Version: 8.18.8
X.Org 6.8
	Download 	11.5 	10/26/05 	Version: 8.18.8


BTW. Big, big tnx...

Edit: I know:
ATI Driver Installer Download 	51.0 	10/26/05 	Version: 8.18.8
:)

ALL WHO HELP'D ME - BIG BIG TNX :)

---

