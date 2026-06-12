---
title: "No youtube videos play in FF or Chrome after upgrade to 16.04"
date: 2016-11-03
forum: General Help
---

### Post by jwhitene on 2016-11-03
After upgrading to 16.04, I can't get any youtube videos to work.  Both Chrome and Firefox refuse to play them.  If I visit this url [https://www.youtube.com/html5](https://www.youtube.com/html5) in firefox, it shows that my browser supports everything.  
HTMLVideoElement
H.264
WebM VP8
Media Source Extensions
MSE & H.264
MSE & WebM VP9
The HTML5 player is currently used when possible.

I have checked that I have the ubuntu-restricted-extras installed.  I also reinstalled the pepper flash and adobe flash plugins.  

I'd rather use html5 over flash, but I do also have the flash plugins installed.  

dpkg -l | egrep 'flash|gnash|spark'
rc  adobe-flashplugin                                           1:20160913.1-0ubuntu0.14.04.1                               amd64        Adobe Flash Player plugin
ii  browser-plugin-freshplayer-pepperflash                      0.3.4-3                                                     amd64        PPAPI-host NPAPI-plugin adapter for pepperflash
ii  pepperflashplugin-nonfree                                   1.8.2ubuntu1                                                amd64        Pepper Flash Player - browser plugin

I also disabled all my FF plugins just in case.

I also found some articles referencing gstreamer and ff, so I installed gstreamer-tools and then set an about:config value in firefox of: media.gstreamer.enabled true.   

Any other ideas?

Whatever happened also seems to have borked my ability to use webex.  I have to now switch out to windows with webex or other similar browser based remote services.

---

### Post by ajgreeny on 2016-11-03
Try removing **pepperflashplugin-nonfree** and keep only the **adobe-flashplugin** and **browser-plugin-freshplayer-pepperflash** packages, which is all that I have and flash or html5 works fine in my 16.04 installations.

I suspect that your system is confused by the overload of different pepperflash packages.

Good luck! Let us know if it works.

---

### Post by mc4man on 2016-11-03
> **jwhitene said:**
> 
I also found some articles referencing gstreamer and ff, so I installed gstreamer-tools and then set an about:config value in firefox of: media.gstreamer.enabled true.   

Any other ideas?
FF doesn't use gstreamer anymore nor is media.gstreamer.enabled an option. Log into a guest session & try YT again in FF or use a fresh profile for FF to check in your user session.

---

### Post by jwhitene on 2016-11-03
547  sudo apt-get remove --purge pepperflashplugin-nonfree
  548  sudo apt-get remove --purge adobe-flashplugin
  549  sudo apt-get remove --purge browser-plugin-freshplayer-pepperflash
  553  sudo apt-get install adobe-flashplugin
E: Package 'adobe-flashplugin' has no installation candidate 
Under software sources, I do have multiverse checked (everything is checked on the ubuntu software tab).  

I was able to install adobe flash using this link though:  [https://apps.ubuntu.com/cat/applications/flashplugin-installer/](https://apps.ubuntu.com/cat/applications/flashplugin-installer/)

  554  sudo apt-get install browser-plugin-freshplayer-pepperflash

Browse to [http://www.dhs.state.il.us/accessibility/tests/flash/video.html](http://www.dhs.state.il.us/accessibility/tests/flash/video.html) with firefox:

gives me an error, I can't make it out completely, because the window is small, but it says something like:
failed to load libpepflashplayer.so
freshwrapper is a translation layer w..(cut off)
ppapi plugin backend.  ensure your sy...
libepepflashplayer.so available.
Paths tried:
bunch of paths.

If I go to [http://isflashinstalled.com/](http://isflashinstalled.com/) it says I have flash installed in firefox.


JavaScript Flash Detection Library

Installed
    Yes
Raw version
    Shockwave Flash 11.2 r202
Major version
    11
Minor version
    2
Revision
    202
Revision string
    r202

Adobe Flash Player Detection Kit (Client)

Type
    Plugin (Non-IE)
Version
    11.2.202

Weird.

---

### Post by CantankRus on 2016-11-04
adobe-flashplugin is in the partner repository.
```
**[COLOR="#006400"]glen@Xenial:~$[/COLOR] apt policy adobe-flashplugin**
adobe-flashplugin:
  Installed: 1:20161026.1-0ubuntu0.16.04.1
  Candidate: 1:20161026.1-0ubuntu0.16.04.1
  Version table:
 *** 1:20161026.1-0ubuntu0.16.04.1 500
        500 http://archive.canonical.com/ubuntu xenial/partner amd64 Packages
        100 /var/lib/dpkg/status
```

Enable Canonical Partners repository in System Settings -> Software & Updates, then run in terminal
```
sudo apt update
sudo apt install adobe-flashplugin
```
I believe this is all you need now.

---

### Post by jwhitene on 2016-11-10
Just an fyi for anyone else confused about what happened, Chrome just recently stopped including the libpepflash...so plugin.   So don't use pepper flash anymore, only use adobe flash plugin.  There is a bug report about this issue.

---

