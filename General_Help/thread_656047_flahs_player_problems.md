---
title: "flahs player problems"
date: 2008-01-02
forum: General Help
---

### Post by fiddilydee on 2008-01-02
total noob***
I want to watch videos on youtube. I install flash player for mozilla, it doesnt work, still get requires flash player, download gnash flash player, it works but it is laggy, even when the video is loaded andthe interface is all messed up, any suggestions????

---

### Post by chewearn on 2008-01-02
You have to manually install from adobe website.

Read this page from bottom up, to find the latest workaround:
[https://bugs.launchpad.net/ubuntu/+source/flashplugin-nonfree/+bug/173890](https://bugs.launchpad.net/ubuntu/+source/flashplugin-nonfree/+bug/173890)

---

### Post by ~LoKe on 2008-01-02
Try this in the terminal...all one line.
```
cd ~/ && wget http://fpdownload.macromedia.com/get/flashplayer/current/install_flash_player_9_linux.tar.gz && tar xzvf install_flash*.tar.gz && cd install_flash* && ./flashplayer-installer
```

Then follow the installer.

---

### Post by fiddilydee on 2008-01-02
i ran the line in terminal ut i havebit ERROR: Your architecture, \'x86_64\', is not supported by the Adobe Flash Player installer.

---

### Post by jespdj on 2008-01-02
You are running 64-bit Ubuntu and there is no 64-bit version of the Flash player. You can't just install the 32-bit version and have it work in your 64-bit browser; you'll need [nspluginwrapper]("http://gwenole.beauchesne.info/projects/nspluginwrapper/") to make the 32-bit Adobe Flash plug-in work in your 64-bit browser.

---

### Post by chewearn on 2008-01-02
Flash 9 install script for AMD64 (nspluginwrapper)
[http://ubuntuforums.org/showthread.php?t=476924](http://ubuntuforums.org/showthread.php?t=476924)

---

