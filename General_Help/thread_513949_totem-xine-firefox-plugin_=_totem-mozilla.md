---
title: "totem-xine-firefox-plugin = totem-mozilla ?"
date: 2007-07-31
forum: General Help
---

### Post by DCboi on 2007-07-31
Hello folks,

Documentation for Ubuntu 7.04 [1] tells to install totem-xine-firefox-plugin package for totem-xine plugin. But totem-xine-firefox-plugin package for feisty refers to totem-mozilla. Are they same ? If not, this documentation may need an update. 

Moreover, can anyone get this plugin working in a browser ? Any sort of feedback is much appreciated :)

[1] [https://help.ubuntu.com/7.04/musicvideophotos/C/onlinemedia.html#onlinemedia-plugins](https://help.ubuntu.com/7.04/musicvideophotos/C/onlinemedia.html#onlinemedia-plugins)

---

### Post by DCboi on 2007-07-31
bump

---

### Post by Seisen on 2007-07-31
It used to be called that in dapper but they phased it out in edgy. So just go ahead and use totem-mozilla it will give you the same functionality. I also filed a bug report so it will get changed.

---

### Post by DCboi on 2007-08-02
Browser recognise the plugin but playback just doesn't work.. I was wondering whether anyone actually got this plugin working. :confused:

---

### Post by Seisen on 2007-08-02
What are you trying to play?

---

### Post by NilsE on 2007-08-02
You may need to install a few other things like most of the Gstreamer 10 stuff and the w32codecs to cover the broad range of audio and video types.

For what Totem does not cover you will need the RealPlayer and RealPlayer plugin (installs with RealPlayer) and Flash plugins.

But first try this site ans see what works and what does not work and go from there.

[http://www.linspire.com/file_types/filetypes.php](http://www.linspire.com/file_types/filetypes.php)

It's nice that Linspire loans this nice testing stuff to us:).

---

