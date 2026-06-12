---
title: "want mplayer instead of totem for firefox"
date: 2007-01-08
forum: General Help
---

### Post by darweth on 2007-01-08
hello...

when i play videos on the web (apple trailers, etc)... they all open in totem.  i installed the mplayer mozilla from the repositories.  how do i make it default to that instead of totem?

---

### Post by WiseElben on 2007-01-08
Perhaps you can just remove totem-mozilla: 
```
sudo aptitude remove totem-mozilla
```

---

### Post by maggotbrain on 2007-01-08
Hey there!

Here are the quick and dirty instructions taken from ubuntuguide:
[]("http://ubuntuguide.org/wiki/Ubuntu:Edgy#How_to_install_Multimedia_Player_.28Mplayer.29_with_plug-in_for_Mozilla_Firefox")

** How to uninstall Totem with plug-in for Mozilla Firefox**

[I]sudo apt-get remove totem-gstreamer-firefox-plugin
[/I]

** How to install Multimedia Player (Mplayer) with plug-in for Mozilla Firefox**

*sudo apt-get install mozilla-mplayer*

If you search for "mplayer in browser" within the forums, you should find some additional info.

Hope this helps.

---

