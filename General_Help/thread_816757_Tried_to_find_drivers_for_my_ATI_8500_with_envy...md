---
title: "Tried to find drivers for my ATI 8500 with envy.."
date: 2008-06-03
forum: General Help
---

### Post by AlexMuller12 on 2008-06-03
i attempted to do the manual install, then i restarted X, and now im in low-graphics mode, and im not sure as to what to do. i hate being an ubuntu newb lol.:confused:

---

### Post by overdrank on 2008-06-03
> **AlexMuller12 said:**
> i attempted to do the manual install, then i restarted X, and now im in low-graphics mode, and im not sure as to what to do. i hate being an ubuntu newb lol.:confused:

HI and can you adjust the resolution via screen resolution located under system, preference. If not you can use the command ```
sudo dpkg-reconfigure -phigh xserver-xorg 
``` in the terminal. If you are using Hardy 8.04 then the drivers that come with the install should work unless you are trying to use compiz-fusion. If so then look here
[http://ubuntuforums.org/showthread.php?t=764633](http://ubuntuforums.org/showthread.php?t=764633)

---

### Post by RAOF on 2008-06-03
I'm fairly sure that your card is no longer supported by ATI's fglrx driver (that you would download with Envy).  On the plus side, just uninstalling the fglrx drivers should get you back to the open source 'ati' drivers, which support your card well - 3d included.  I believe that Compiz should work without tweaks, too, but I'm not sure - if this is in a laptop your card may be blacklisted because of driver bugs exposed by Compiz.  If that is the case, follow the link in the above post to disable the blacklist (but don't be surprised if strange things happen ;)).

---

### Post by AlexMuller12 on 2008-06-03
i attempted using the command you gave me and it spit this back at me:

xserver-xorg postinst warning: overwriting possibly-customised configuration
   file; backup in /etc/X11/xorg.conf.20080603021200


doesnt sound too good to me 

im not too sure how to uninstall what envy installed..any help with that? is it in the package manager?

---

### Post by RAOF on 2008-06-03
Envy (at least in Hardy) should be able to uninstall what it installed.  Start there.

---

### Post by AlexMuller12 on 2008-06-03
should i just uninstall the 2 parts of envy from the synaptic package manager

---

### Post by AlexMuller12 on 2008-06-03
bumperuski :)

---

### Post by RAOF on 2008-06-03
> **AlexMuller12 said:**
> should i just uninstall the 2 parts of envy from the synaptic package manager

No; you should load up Envy and hit the "uninstall" button which I hope/believe is there.

---

### Post by AlexMuller12 on 2008-06-04
hm..i dont think i have the GUI installed..i did it all in terminal.

EDIT: im in Ubuntu now..and the resolution is back (1280 x 1024)..i dont know how though lol.. and i went to System>Prefs>Appearance and went to Visual Effects and clicked Advanced and tried Normal and its still laggy..im assuming its still using envy's drivers?

EDIT 2: I found the program, im retarded :P
uninstalled..rebooting now :)

Edit 3: the uninstall didnt seem to do anything, its still laggy on Normal and Advanced :(

---

### Post by AlexMuller12 on 2008-06-04
bump

---

### Post by AlexMuller12 on 2008-06-10
i dont mean to break the rules, but i still cannot solve this problem and it makes it hard to use ubuntu :(

---

