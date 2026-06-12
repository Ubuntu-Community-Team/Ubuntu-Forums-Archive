---
title: "Pepper Flash not Working in Firefox"
date: 2016-11-28
forum: General Help
---

### Post by eternalstorm44 on 2016-11-28
Hi guys,
So I have the newest version of chrome installed and I've been trying to get firefox working using Pepper Flash so that I can watch HBO go. I seem to have done something because now whenever I try to load a video in HBO Go I get the error message below. I'm pretty new to Linux and before I installed Ubuntu I was just your basic mac user with no computer skills so I could really use the help with this one. I'm just starting to learn how the terminal works.  

> [COLOR=#000000]*Failed to load "libpepflashplayer.so".*[/COLOR]
[COLOR=#000000]*Freshwrapper is a translation layer which needs*[/COLOR]
[COLOR=#000000]*PPAPI plugin backend. Ensure your system have*[/COLOR]
[COLOR=#000000]*"libpepflashplayer.so" available.*[/COLOR]
[COLOR=#000000]*Paths tried:*[/COLOR]
[COLOR=#000000]*/opt/google/chrome/PepperFlash/libpepflashplayer.so*[/COLOR]
[COLOR=#000000]*/opt/google/chrome-beta/PepperFlash/libpepflashplayer.so*[/COLOR]
[COLOR=#000000]*/opt/google/chrome-unstable/PepperFlash/libpepflashplayer.so*[/COLOR]
[COLOR=#000000]*/usr/lib/adobe-flashplugin/libpepflashplayer.so*[/COLOR]

---

### Post by Dennis N on 2016-11-28
I don't think Firefox can use pepper flash. Only chrome or chromium browsers can.

---

### Post by Frogs Hair on 2016-11-28
I've not used Pepper with Firefox, but have used the following though not at the same time. I can view some promo video from the HBO site with the first option listed , but can't test an actual movie or show.

```
sudo apt-get install flashplugin-installer 
``` or ```
sudo apt-get install adobe-flashplugin
```

---

### Post by &amp;KyT$0P# on 2016-11-28
Where did you put [FONT=Courier New]libpepflashplayer.so[/FONT]?  You'll need to edit [FONT=Courier New]~/.config/freshwrapper.conf[/FONT] and change the [FONT=Courier New]pepperflash_path[/FONT] setting to the **full** path to [FONT=Courier New]libpepflashplayer.so[/FONT].

If [FONT=Courier New]~/.config/freshwrapper.conf[/FONT] doesn't exist, create it as a text file and check [here]("https://github.com/i-rinat/freshplayerplugin/blob/master/data/freshwrapper.conf.example") for an example.  If you start with that example as-is, don't forget to uncomment the [FONT=Courier New]pepperflash_path[/FONT] line before changing it.

---

### Post by Dennis N on 2016-11-28
I should amend my answer: Firefox alone can't use pepper plash - that is correct, but there is the plugin freshplayer. See if this article helps you out. I think I even tried it once, but I could not log into some sites, so abandoned it.

[http://ubuntuhandbook.org/index.php/2015/10/ipepper-flash-for-firefox-ubuntu-15-10/](http://ubuntuhandbook.org/index.php/2015/10/ipepper-flash-for-firefox-ubuntu-15-10/)

---

### Post by launchpad-net-sifter on 2016-12-19
Chrome has started installing pepperflash in the users' home directories instead of where freshwrapper is used to looking for it.

halogen2's response above is correct, you can fix it by editing ~/.config/freshwrapper.conf to point to the .so file installed by chrome.

You will need to [apt-get] install chrome [google-chrome-stable] for this to work (even though we are ultimately making this work in firefox... You don't actually need to run chrome, except maybe once to cause it to pull in pepperflash), as well as browser-plugin-freshplayer-pepperflash .   The pepperflashplugin-nonfree package, which in theory would work instead of installing chrome, appears to be broken.

Once you're installed freshplayer, you can find a template of freshwrapper.conf in /usr/share/doc/browser-plugin-freshplayer-pepperflash/freshwrapper.conf.example most likely.

I copied that file to ~/.config/freshwrapper.conf and then changed just one line to this:

pepperflash_path = "/home/[myusername]/.config/google-chrome/PepperFlash/24.0.0.186/libpepflashplayer.so"

You'll need to see exactly what path your libpepflashplayer.so is at...

This is a short term solution since presumably updates to chrome could move this (i.e., if 24.0.0.186 is a build number, this is likely to change often).  Hopefully freshwrapper will be updated to look in ~/.config/google-chrome/... soon and this fix will become unnecessary (at which point you'll need to delete freshwrapper.conf again to enable the proper behavior...)

---

