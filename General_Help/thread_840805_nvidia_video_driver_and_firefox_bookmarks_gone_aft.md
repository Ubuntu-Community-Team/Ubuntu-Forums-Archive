---
title: "nvidia video driver and firefox bookmarks gone after update.."
date: 2008-06-25
forum: General Help
---

### Post by Mia_tech on 2008-06-25
after doing two updates, two days in a row, my nvidia video driver is gone, now my display is booting to 800X600, and the restricted video driver for nvidia is not showing up...also my bookmarks in firefox are gone...the bookmarks I could restore, but how could I get my video back working the way it was?

any help appreciated

thanks

---

### Post by phidia on 2008-06-25
First try the easy things like checking your /etc/X11/ for a back up of the previous working xorg.conf. If you find an xorg.conf.bak there try moving that to the active xorg.conf and restarting x (Alt+Ctrl+backspace).
If there isn't any back up xorg.conf-which would be strange-then you need to look at [howtos]("http://ubuntuforums.org/showthread.php?t=301499") for installing your nvidia driver.

---

### Post by Mia_tech on 2008-06-25
I have restored what it seemed a good backup of the xorg.conf file, but it didn't have the .bak extension...
xorg.conf                 
xorg.conf.1               
xorg.conf.2               
xorg.conf.20080512202624  
xorg.conf.failsafe       
xorg.conf.failsafe.bak 

I restored from the 4th file on the list, but it went back to 800x600, and the driver still missing from the restricted drivers...I think, the driver is gone and I may have to reinstall...

by the way the "howto" you linked above is for version upto 7.10...and I'm using hardy.

thanks

---

### Post by drs305 on 2008-06-25
For the nvidia drivers, I used envyng-gtk to install it. It worked very well and is in the repositories, or:
```
sudo aptitude install envyng-gtk
```

Once installed, it's in the System Tools menu. There is also an Nvidia X Server Settings wizard in System, Admin.

---

### Post by Mia_tech on 2008-06-25
I've installed envyng-gtk, and run the automatic detection, but it prompt me for the cd, I insert the cd, but it keeps asking me for the cd, and ubuntu is mounting the cd as I'm seen it on the desktop, btw the Nvidia X Server .. is no where to be found

any ideas?

thanks

---

### Post by drs305 on 2008-06-25
> **Mia_tech said:**
> I've installed envyng-gtk, and run the automatic detection, but it prompt me for the cd, I insert the cd, but it keeps asking me for the cd, and ubuntu is mounting the cd as I'm seen it on the desktop, btw the Nvidia X Server .. is no where to be found

any ideas?

thanks

**Added**: I probably misunderstood which cd it is asking for. I'll leave the post just in case the response below applies. If it's not the hardy cd, which cd is it asking for.

You probably still have the install cd listed as a source in synaptic. Open synaptic, settings, repositories. In the Ubuntu Software tab, uncheck the lower box for the Ubuntu cdrom. 

Now you shouldn't be prompted for the cd and synaptic will go straight to the online repositories.

---

### Post by Mia_tech on 2008-06-26
finally got it working, was the cd option in synaptic, I wanted to ask you what is the difference between the nvidia drivers that offer nvidiang-gtk and the one that comes in the restricted driver?, that one showed up when I installed my system for the first time

thanks

---

### Post by drs305 on 2008-06-26
> **Mia_tech said:**
> finally got it working, was the cd option in synaptic, I wanted to ask you what is the difference between the nvidia drivers that offer nvidiang-gtk and the one that comes in the restricted driver?, that one showed up when I installed my system for the first time

thanks

I did some checking and it appears envyng-gtk ccurrently installs version 173.14.05 while the normal restricted driver version is an earlier one - 169.12.

By the way, the Nvidia X Server Configuration tool available through System, Admin, Tools appears to be the nvidia-settings package in synaptic if it didn't get installed via envyng.  :)

---

