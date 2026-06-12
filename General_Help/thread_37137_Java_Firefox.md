---
title: "Java Firefox"
date: 2005-05-26
forum: General Help
---

### Post by Swazi on 2005-05-26
Hi

I normally do a "ln -s /pathtojava /home/swazi/.mozilla/firefox/plugins" to that effect and get my java working on Firefox. Does not seem to work this time on Ubuntu Hoary the Hedgehog.

Any tips ?

---

### Post by pdk001 on 2005-05-26
check here [http://www.ubuntuguide.org/#jre](http://www.ubuntuguide.org/#jre)

---

### Post by pdk001 on 2005-05-26
* Installing Java for Firefox internet browser
Ubuntu Addon Package: 
[http://www.mrbass.org/linux/ubuntu/](http://www.mrbass.org/linux/ubuntu/)

After you have Java installed, enter the following code into your root terminal: 
cd /usr/lib/mozilla-firefox/plugins
ln -s /usr/java/jre1.5.0_02/plugin/i386/ns7/libjavaplugin_oji.so

source : [http://www.ubuntuforums.org/showthread.php?t=36817](http://www.ubuntuforums.org/showthread.php?t=36817)

---

