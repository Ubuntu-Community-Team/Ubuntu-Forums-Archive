---
title: "Flash problem"
date: 2007-10-19
forum: General Help
---

### Post by Malkosha on 2007-10-19
Downloading...
--13:35:14--  [http://fpdownload.macromedia.com/get/flashplayer/current/install_flash_player_9_linux.tar.gz](http://fpdownload.macromedia.com/get/flashplayer/current/install_flash_player_9_linux.tar.gz)
           => `./install_flash_player_9_linux.tar.gz'
Resolving fpdownload.macromedia.com... 1.0.0.0
Connecting to fpdownload.macromedia.com|1.0.0.0|:80... failed: Connection timed out.
Retrying.

Welcome to my loop! This goes on and on and while synaptic swears flash is already installed, it doesn't work. Strange it would resolve the address to 1.0.0.0 but thats what it does.

I have tried Automatix2, Synaptic, downloading the files from adobe and going manual and this is the best I can get. It's been going on for two days now and is very frustrating.

Anyone have any ideas? I am willing to reinstall and even pour water into the case while the machine is running. :lolflag:

ThX!!

---

### Post by NilsE on 2007-10-19
All you need to do is install   flashplugin-nonfree    in synaptic and you should be good to go.

If it is already installed, remove it and install it again.

---

### Post by Malkosha on 2007-10-19
> **NilsE said:**
> All you need to do is install   flashplugin-nonfree    in synaptic and you should be good to go.

If it is already installed, remove it and install it again.

Thanks but its the same. The uninstall went smooth but after an attempt to reinstall, it starts looping again because it can't seem to connect to fpdownload.macromedia.com.

---

### Post by Malkosha on 2007-10-19
> **Malkosha said:**
> Thanks but its the same. The uninstall went smooth but after an attempt to reinstall, it starts looping again because it can't seem to connect to fpdownload.macromedia.com.

Spoke too soon!

I opened up the term window in synaptic and hit CTRL-C to break the loop and it reported that Falsh was installed. I tested it out and it now worked fine. Weird but thanks!

---

