---
title: "Keyboard layout disappears"
date: 2008-06-17
forum: General Help
---

### Post by thorbjornw on 2008-06-17
Alternate keyboards suddenly disappered yesterday.  I have Ubuntu 8.04 installed on my Vaio VGN750N, and it has been working well.  I work in several languages and therefore use 3 keyboard layouts (US, Spanish and Danish).  The keyboard applet continues to be there showing the three keyboards, but only the US keyboard is working.  To get them back, I have to go into Sytem/tools/preferences/keyboards, restore default (only US) and then reinstall the Spanish and Danish keyboards.  It then works normally, but disappears again after each reboot.  Are there any solutions or will I have to reinstall Ubuntu to solve it?

---

### Post by mortenoc on 2008-06-26
I have the precise same problem on my Asus laptop. It seems that Ubuntu over writes any changes in the language settings on startup.

---

### Post by thorbjornw on 2008-06-26
Keyboard switching can be solved editing the xorg.conf as described in [https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-input-keyboard/+bug/196277](https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-input-keyboard/+bug/196277)

Edit your xorg.conf: sudo gedit /etc/X11/xorg.conf

The keyboard section should look like this:

Section "InputDevice"
   Identifier "Generic Keyboard"
   Driver "kbd"
   Option "CoreKeyboard"
   Option "XkbRules" "xorg"
   Option "XkbModel" "pc105"
   Option "XkbLayout" "us,XX"
   Option "XKbOptions" "grp:alt_shift_toggle"
EndSection

The two changes to make are:
(1) under "XkbLayout", replace "us" with "us,XX", where XX is the ISO country code for the alternate language(country codes can be found at [http://www.iso.org/iso/support/country_codes/iso_3166_code_lists/iso-3166-1_decoding_table.htm](http://www.iso.org/iso/support/country_codes/iso_3166_code_lists/iso-3166-1_decoding_table.htm)). You can add more codes if you want, separated by a comma (I have three:  US, DK, ES).
(2) ad the line
Option "XKbOptions" "grp:alt_shift_toggle" 

Then it works, also after reboot.

At the same page, somebody mentions that the problems is related to automated log-in, so if you go back to normal log-in the problem disappears.  I have not tried that.
then you can shift between alternate keyboards with alt-shift (as in Windows).

---

### Post by mortenoc on 2008-06-26
Thanks. I have also found this thread, which solved my problem.

Saludos
Morten

---

### Post by mitshi on 2008-08-30
I'm sorry, I'm new to ubuntu, and to linux generally.
I'm using 3 layouts, and got the same problem, I tryed to change it and got this message: 
"You do not have the permissions necessary to save the file. Please check that you typed the location correctly and try again."

Where do I get the permission needed?

P.S. I tryed giving all the permissions to the user and still the same message.
](*,)

---

### Post by mortenoc on 2008-08-31
> **mitshi said:**
> I'm sorry, I'm new to ubuntu, and to linux generally.
I'm using 3 layouts, and got the same problem, I tryed to change it and got this message: 
"You do not have the permissions necessary to save the file. Please check that you typed the location correctly and try again."

Where do I get the permission needed?

P.S. I tryed giving all the permissions to the user and still the same message.
](*,)
You properly have to edit /etc/X11/xorg.conf as root or superuser. I usually use krusader en root mode to edit configuration files. 
Otherwise use gedit as Thorbjornw suggests: type "sudo gedit /etc/X11/xorg.conf" in a terminal.

---

### Post by mitshi on 2008-09-01
Thanks, but I'm not that new :)
I got the message when I tried that.

I don't know how to login to root or as administrator, or something..

---

### Post by mortenoc on 2008-09-03
Are you using the sudo command like in the example in my last post?

---

### Post by mitshi on 2008-09-04
Yes, but how do I enter the "root mode" or as "superuser"?

---

### Post by thorbjornw on 2008-09-04
Every command you enter starting with "sudo" means that you are superuser (Super User DO).  You will be asked for your password before the command is executed to make sure you have the permission.

---

### Post by mitshi on 2008-09-04
Thank you. I don't know what was the the problem but it solved.

Say can I also change the the variant of layouts? 
I need the russian keybord to be - phonetic, and its give only the default in that case..

---

### Post by thorbjornw on 2008-09-04
No idea.

---

### Post by mitshi on 2008-09-04
Thanks anyway.

---

