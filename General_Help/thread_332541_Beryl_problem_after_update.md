---
title: "Beryl problem after update"
date: 2007-01-06
forum: General Help
---

### Post by Peti29 on 2007-01-06
I've commited an update in wich some Beryl components were also updated.
Now when I start Beryl some error messages appear and no splash screen is displayed.
Apart from that it still works but I feel some discomfort about the error and would like to fix it if I can.
Below is the error message:
```
peti29@Peti29-desktop:~$ beryl-manager
peti29@Peti29-desktop:~$ XGL Present

** (process:5880): WARNING **: get_setting_is_integrated not found in backend ini

** (process:5880): WARNING **: get_setting_is_read_only not found in backend ini
beryl-xgl: Couldn't load plugin 'bs'

** (process:5880): WARNING **: get_setting_is_integrated not found in backend ini

** (process:5880): WARNING **: get_setting_is_read_only not found in backend ini
Initiating splash
beryl-xgl: Failed to load slide: /usr/share/beryl/cubecaps.png
beryl-xgl: Failed to load slide: /usr/share/beryl/cubecaps.png
Reloading all options.
[SPLASH]: Could not load splash background image "/usr/share/beryl/splash_background.png" !
[SPLASH]: Could not load splash logo image "/usr/share/beryl/splash_logo.png" !

```
The "Couldn't load plugin 'bs'" part I remember seeing earlier aswell so that didn't emerge from my last update. However I'd like to fix this too.

Also when searching for updates I receive this message (don't know if that has to do with the splash screen issue or not):
```
W: GPG error: http://ubuntu.beryl-project.org edgy Release:
The following signatures couldn't be verified because the public key is not available:
NO_PUBKEY 3FF0DB166A7476EA
```

I'm new to Linux so I'd really appreciate some help, thx in advance!

---

### Post by Waappu on 2007-01-08
Hi

There is some problem in repository key. Try this

```
wget http://ubuntu.beryl-project.org/root@lupine.me.uk.gpg -O- | sudo apt-key add -
sudo apt-get update
sudo aptitude upgrade
```

---

### Post by Peti29 on 2007-01-10
Thx! That fixed the security warning. However the error when beryl-manager starts still shows (no splash screen too).
I tryed
```
apt-get install beryl beryl-core libberylsettings0 beryl-plugins beryl-settings beryl-manager emerald emerald-themes
```
but that found nothing new to install.
Is there a way to completely reinstall beryl?

---

### Post by Waappu on 2007-01-10
Hi

To uninstall 
```
sudo aptitude purge beryl
```

Then you could try to install again. I used this guide
[http://wiki.beryl-project.org/index.php/Install/Ubuntu/Edgy/AiGLX](http://wiki.beryl-project.org/index.php/Install/Ubuntu/Edgy/AiGLX)
and extra repo from here
[http://3v1n0.tuxfamily.org/dists/edgy/beryl-svn/](http://3v1n0.tuxfamily.org/dists/edgy/beryl-svn/)

---

