---
title: "lost password &amp; username"
date: 2007-07-09
forum: General Help
---

### Post by grimmjimm on 2007-07-09
I have just installed ubuntu 7.04. i started the install and just let my pc do its thing.
everthing seems okay, boots okay, but here is the rub. 
It askes me for a username & password, I didn't install either, so where do i go from here.
All help would be appreciated.:confused:

---

### Post by AlexenderReez on 2007-07-09
:lolflag::lolflag:

it is quite impossible either....hm....are you forgot or something,there must be time when you insert password and username while install ubuntu ...(i don't if you use windows migration tool,but normal will ask)...by the way....


> [http://news.softpedia.com/news/Resetting-a-Forgotten-Root-Password-40544.shtml](http://news.softpedia.com/news/Resetting-a-Forgotten-Root-Password-40544.shtml)

---

### Post by ramjet_1953 on 2007-07-09
As a part of the install, it would have asked you for a user name and password.

These are what you use.

However, if the system was set-up as an OEM system, you can try oem for username and password.

If this works you can then set-up a "proper" user by typing this command into a terminal:

[COLOR="Red"]sudo oem-config-prepare[/COLOR]

However, if the above is not your problem, you can do the following:

1. Turn your computer on and press [COLOR="Blue"]ESC[/COLOR] at the grub prompt

2. Press [COLOR="Blue"]e[/COLOR] for edit

3. Highlight the line that begins with kernel and press [COLOR="Blue"]e[/COLOR] again

4. Go to the end of the line and add [COLOR="Blue"]rw init=/bin/bash[/COLOR]

5.Press [COLOR="Blue"]ENTER[/COLOR] and then press b to boot your system

6. To change your password type [COLOR="Blue"]passwd <username> [/COLOR]

7. Type [COLOR="Blue"]reboot [/COLOR]to reboot your system

I hope that this helps.

Regards,
Roger :cool:

---

### Post by nelno on 2007-07-13
I am having this same problem with 7.04.

I sat in front of the PC for duration of the boot process.  I was never asked for a username or password until Ubuntu finished booting and the actual login prompt appeared.

I thought that I simply chose "Start or Install Ubuntu".

However, before actually booting I tried out the F1 key to read the help.  I also hit F6 for "Other Options" which brought up a boot command line which I could not seem to get rid of.  However, up and down arrows still moved the main menu selection so I chose "Start or Install Ubuntu" and hit return.  Perhaps having brought up the boot command line has something to do with this, because as far as I can tell I simply downloaded the desktop version (ubuntu-7.04-desktop-i386.iso) and didn't specifically select OEM anything at any point.

I was only checking out the help and options because Ubuntu locked the PC on my first attempt to boot from CD. 

"oem" for the username and password is not allowing me to log on so I've no choice but to go through the long boot process again and hope that the third time is the charm.

---

