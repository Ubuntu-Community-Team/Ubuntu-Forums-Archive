---
title: "Cant increase screen resolution."
date: 2008-05-28
forum: General Help
---

### Post by obts10 on 2008-05-28
Hi, Im a total Linux noob and just installed Ubuntu 8.04 the other day on an old Celeron PC that i was given. I decided to learn more about Linux and to see if its for me after reading books and magazines for a few months.

Anyway, the install went very smoothly (SUSE 10.3 would crash) and the computer is working well with this new OS. It really struggled with XP. The only thing is that i can't increase the screen resolution beyond 856*600. There are no greater resolutions to select for some reason. In the documentation for my monitor it says that its capable of displaying 1280*768@60Hz.

I really don't know what to do, and couldnt find anything on the web after a few days of searching. Does anyone know if it is possible for such an old computer to have a higher resolution than this in Linux?

I have a:
- Celeron 1200mhz
- 256 mb of RAM (16mb of this shared with video)
- ASUS TUSI-M motherboard
- SiS 630ET chipset
- SiS300 AGP graphics controller

---

### Post by justleen on 2008-05-28
you should run ```
sudo  dpkg-reconfigure xserver-xorg 
``` from a terminal.

This will ask a lot off questions, leave tem to default. When you get to the part of the display, make sure you enable the higher resultions you want to use.
Once done, restart X (ctrl-alt-bkspace) you should have more resolutions now

---

### Post by pjpeter on 2008-05-28
In terminal type>

sudo gedit /etc/X11/xorg.conf


then add this line under configured monitor

modeline "1280x768@60"

this works for me:

Section "Monitor"
Identifier "Configured Monitor"
Vendorname "Plug 'n' Play"
Modelname "Plug 'n' Play"
modeline "1600x1200@60" 
EndSection

-Make sure you save a backup of the original conf file!

---

### Post by housam on 2008-05-28
try this way it may help

```
sudo nano /etc/usplash.conf
```

 you will got something like that 


> # Usplash configuration file
# These parameters will only apply after running update-initramfs.
  



add the required resolution 



> # Usplash configuration file
# These parameters will only apply after running update-initramfs.
xres=[COLOR="Red"]1280[/COLOR]
yres=[COLOR="red"]768[/COLOR] 



OR put the settings you want for [COLOR="red"]x & y[/COLOR] then reboot and type :

```
sudo dpkg-reconfigure usplash
```
 then check for the new settings -- System > Preferences > Screen Resolution and select the new one.
__________________

---

### Post by obts10 on 2008-05-28
Thanks for the replies to my question, ill give these commands a go tonight when i get back from work. Ill cross my fingers that one of these works.

---

