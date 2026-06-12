---
title: "Start-up/Shutdown Animation gone. HELP!"
date: 2007-03-04
forum: General Help
---

### Post by bash on 2007-03-04
I installed Ubuntu on a different machine. It was Edgy. And for some reason instead of the normal boot-up and shutdown animation (the ubuntu and a loading/unloading orange bar) I only get a blinking  _  in the top left corner of the screen. Besides that Ubuntu works perfectly normal, it starts and also shuts down correctly. I tried the Startup Manager (SUM) and set the startup theme there. But that didn't help either. Anyone knows whats going on?

---

### Post by bloodniece on 2007-03-04
Maybe:

```
sudo apt-get install bootsplash-theme-debian
```

---

### Post by bash on 2007-03-05
Installed it. Still get the blinking _ in the top left corner. Funny thing is that when I start from the Live CD I also only get the _ instead the normal startup animation. But if I start the Live CD in ma comp everything is normal.

---

### Post by seldenthuis on 2007-03-05
Try```
sudo dpkg-reconfigure usplash
```

That reconfigures the splash screen and may make it come back. If that doesn't work, post the contents of /etc/usplash.conf.

Usplash defaults to your screens native resolution, but that does not always work. I have a Dell Latitude D820 with a 1920x1200 screen, but I have to set the usplash resolution to 1024x768 to make it work.

---

### Post by strabes on 2007-03-05
[http://strabes.wordpress.com/2007/02/17/change-bootsplash-images-in-ubuntu/](http://strabes.wordpress.com/2007/02/17/change-bootsplash-images-in-ubuntu/)

---

### Post by bash on 2007-03-06
Ok seldenthuis I did what you said. Didn't help. I even changed the resolution in the usplash.conf to 1024 * 840. Still didn't work.

This is how my usplash.conf looks like:

> # Usplash configuration file
xres=1280
yres=1024


---

