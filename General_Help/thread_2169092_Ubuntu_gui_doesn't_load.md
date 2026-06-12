---
title: "Ubuntu gui doesn't load"
date: 2013-08-20
forum: General Help
---

### Post by shemeshra on 2013-08-20
Hey all, today after i updated ubuntu base and restarted i have a problem. 
After i login to unity, it seems like it doesn't load at all.. I tryed this:
```
dconf reset -f /org/compiz/ 
unity --reset-icons &disown
```
I restarted but it does nothing. I tryed to login with cinnamon, it gives me an error and wants to restart, after a couple of restarts (cinnamon) it loads, but still gives me the same error.. 

thx for help

**UPD:**
Ubuntu 13.04, just a small update

---

### Post by SweetAurora on 2013-08-20
Which Ubuntu are you using? Did you upgrade to a new release from an older one, or did you just do a simple update?

---

### Post by shemeshra on 2013-08-20
Sorry, forgot to write it.. It's 13.04, it was small update ~50mb ubuntu base.

---

### Post by SweetAurora on 2013-08-20
Do you still have access to a terminal? on the keyboard, hold ctrl+alt+t to open it and type 
```
sudo apt-get update && sudo apt-get dist-upgrade
```
but on the dist-upgrade, don't push y, instead copy the output from the command, push n, and then type
```
firefox
``` 
in terminal to open Firefox and paste it here in a reply. Use the code tags please when doing so.

---

### Post by shemeshra on 2013-08-20
Yes, I still have access to terminal, but I don't have any dist updates, so there is no Y/N .. 
Btw, i can access to gnome2-fallback and it works without any error.

---

### Post by SweetAurora on 2013-08-20
Then it's probably a graphics error. What graphics card are you using? If it's an ATI or Nvidia, how did you install the drivers?
Post the output here:
```
lspci | grep VGA
```

---

### Post by shemeshra on 2013-08-20
ATI, i've installed the driver from their website.

The [COLOR=#000000][FONT=Ubuntu Mono]lspci | grep VGA :
02:00.0 VGA compatible controller: Advanced Micro Devices [AMD] nee ATI Park [Mobility Radeon HD 5430/5450/5470][/FONT][/COLOR]

---

### Post by SweetAurora on 2013-08-20
You were not supposed to do that!!! **NEVER USE THE DRIVER ATI SUPPLIES ON THEIR WEBSITE!!! **Because it is untested by Canonical and usually requires manually reinstalling every time you update the kernel and any graphics libraries like MESA and X.Org.

You will have to uninstall the driver you downloaded, remove the X.Org config file it likely created, then install the driver Ubuntu provides in the driver utility.
I'm not fully litterate on ATI cards and drivers so someone else will have to step in.

---

### Post by shemeshra on 2013-08-20
Thx for helping me, changed the driver and it solved the problem :)

---

### Post by SweetAurora on 2013-08-20
Well good! You are welcome. :)

---

