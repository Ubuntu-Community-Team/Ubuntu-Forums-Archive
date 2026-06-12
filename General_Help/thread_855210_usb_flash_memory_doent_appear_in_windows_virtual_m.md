---
title: "usb flash memory doent appear in windows virtual machine by virtual box"
date: 2008-07-10
forum: General Help
---

### Post by lycopenehead on 2008-07-10
i hope i didnt post in the wrong category,
please anyone help me i have ubuntu 8.04 that hosts virtualbox ose with win xp on it
when i plug my flash memory drive or my mp3 player it doesnt appear in the  my computer how i can make that happen,i want to update my firmware of my mp3 player so it requires that it should appear in my computer ,in the mean while the mp3 manufacturer doesnt support linux in that matter:confused:

---

### Post by ubuscout on 2008-07-10
> **lycopenehead said:**
> i hope i didnt post in the wrong category,
please anyone help me i have ubuntu 8.04 that hosts virtualbox ose with win xp on it
when i plug my flash memory drive or my mp3 player it doesnt appear in the  my computer how i can make that happen,i want to update my firmware of my mp3 player so it requires that it should appear in my computer ,in the mean while the mp3 manufacturer doesnt support linux in that matter:confused:

...first checkout dummy questions. Have u activated usb device in the virtualbox application ? (host side) 

..aftr that, have u right to usbfs ? 

I had same problem and I modified my fstab line so:

"none                 /proc/bus/usb        usbfs      devgid=1000,devmode=664 0 0"

gid ofcourse could be yours..
(without quote)

bye

---

### Post by andrewbrown22 on 2008-07-10
> **lycopenehead said:**
> i hope i didnt post in the wrong category,
please anyone help me i have ubuntu 8.04 that hosts virtualbox ose with win xp on it
when i plug my flash memory drive or my mp3 player it doesnt appear in the  my computer how i can make that happen,i want to update my firmware of my mp3 player so it requires that it should appear in my computer ,in the mean while the mp3 manufacturer doesnt support linux in that matter:confused:

USB support is not enabled in VirtualBox OSE. You must download the binaries from the website to install the non-open source version and then take a look at [this page](http://ubuntuforums.org/showthread.php?p=5224346) to get usb to work. It works great for me to sync my WinMo 6 phone with Outlook from within my Ubuntu install.

---

### Post by ubuscout on 2008-07-11
Sorry <lycopenehead>  ... I've mis-read u meant virtualbox ose ...yes, that doesn't support usb... Ihad usb problem with "not ose" version and I workaround them in the way I wrote u up...

bye

---

