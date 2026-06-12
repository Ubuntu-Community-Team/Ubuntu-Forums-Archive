---
title: "The best way to install Adobe Flash"
date: 2015-07-02
forum: General Help
---

### Post by tech291083 on 2015-07-02
Hi Friends,

I have just started using Ubuntu 14.04.2 Desktop 32 bit. I would like to know whether Software Center is the only way to install Adobe Flash Player. Thanks.

---

### Post by llamabr on 2015-07-02
[https://wiki.ubuntu.com/Chromium/Getting-Flash](https://wiki.ubuntu.com/Chromium/Getting-Flash)
[http://askubuntu.com/questions/341428/how-to-install-flash-player-on-ubuntu](http://askubuntu.com/questions/341428/how-to-install-flash-player-on-ubuntu)

---

### Post by efflandt on 2015-07-02
Instead of Chromium, you can get Google Chrome browser right from Google which includes their pepper flash. Google Chrome also works with Netflix, but I think you have to set your Profile on Netflix website to "Prefer HTML5" (normally Netflix was using Microsoft Silverlight which gets more involved trying to run under wine).

But for Firefox I typically install **Ubuntu Restricted Extras** using either Ubuntu Software Center (or **sudo apt-get install ubuntu-restricted-extras** in a terminal) which includes flashplugin-installer package and various audio/video codecs.

---

### Post by VMC on 2015-07-02
If your asking about Firefox, I don't know the correct method. I do it this way.

I get the latest 'so' file first, which right now is "Version 11.2.202.468". Then:```
sudo cp libflashplayer.so /usr/lib/mozilla/plugins
```.

edit: To check, go to Add-ons Manager and Check You Plugins to be sure.

---

### Post by mattharris4 on 2015-07-03
Adobe Flash for Linux is horribly out of date.  However, you can install Pepper Flash and in my experience it works with both Chromium and Firefox (Pepper Flash working with Firefox is relatively new so articles may state it does not work if they have not been updated).  The install instructions have also changed as of May 2015.  Instructions are here:  
[https://wiki.ubuntu.com/Chromium/Getting-Partner-Flash](https://wiki.ubuntu.com/Chromium/Getting-Partner-Flash) .

---

