---
title: "Ubuntu 16.04 freezes after locking screen"
date: 2018-12-12
forum: General Help
---

### Post by giobaxx on 2018-12-12
Hello 

I'm back for a new issue. Basically an Ubuntu 16.04 time to time freeze after lock the screen. Basically you lock the screen and when you try to login again the workstation freeze. 

we tried to disable following this guide:

 ```
[COLOR=#0000cd]the [FONT=Consolas]sudo -H gedit /var/lib/polkit-1/localauthority/10-vendor.d/com.ubuntu.desktop.pkla[/FONT][/COLOR][COLOR=#242729][FONT=Arial]
Scroll to the bottom. Check to see if the following information exists, and if not add them:[/FONT][/COLOR]
[COLOR=#0000cd][Disable suspend]
Identity=unix-user:*
Action=org.freedesktop.upower.suspend
ResultActive=no
[/COLOR]
```

But this not solve the issue, and we don't know what we can do. do you have any idea where to look? 

i was thinking to try to install Gnome to see if the problem is Unity but i don't know if it could be a solution...

---

### Post by Furycd001 on 2018-12-13
This may not help or be of any use, but anyway.. I have a macbook that is running a custom Ubuntu 16.04 install. Ever time I would put the laptop to sleep or would lock it / close the lid, the display would never want to turn back on & the laptop was basically frozen as such. I had to hold down the power button for whatever seconds & hard rebooted the system whenever this happened. The problem went away whenever someone told me to install **xautolock**....

---

