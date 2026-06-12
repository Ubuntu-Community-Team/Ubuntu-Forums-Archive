---
title: "Flash 9 not working correctly in Firefox"
date: 2006-11-15
forum: General Help
---

### Post by fettuohi on 2006-11-15
I'm runningKubuntu Edgy on my machine and I have installed the flash-plugin via Automatix2. My problem is that on certain webpages in Firefox-2.0 flash doesn't work like

[www.ebay.com](www.ebay.com)
tv2.dk
[www.ebay.de](www.ebay.de).

In the place where the flash add should be I only see white background. Funny thing is that the plugin works fine with Opera 9.02. On my laptop I'm running FC5 and there the same plugin works in Firefox 2.0.Anybody got any ideas. I have the same issue with FF 2.0 on win XP.

Regards

André

---

### Post by yopnono on 2006-11-15
Uninstall the Flash and then install it manually

---

### Post by fettuohi on 2006-11-15
Tried it, doesn't work. Problem still percists :(.

Regards

André

---

### Post by ajgreeny on 2006-11-15
Does your *firefox, about:plugins* show the plugin as installed?  I tried doing it myself and got a problem with either the version still showing as 7, not 9, or not showing at all.  I ended up by backing up the old versions of *libflashplayer.so* as *libflashplayer.so~* and then copying the new version 9 of *libflashplayer.so* into the several places where it was before.  On my system there are many links to the actual file *libflashplayer.so* (in /usr.lib/flashplugin-nonfree) and I had to change all of them for some reason to the actual file rather than the links they were before in order to get it to work as v9.  Very strange, but it works great now.

Try downloading the flash player 9 plugin installer from adobe, direct.  I downloaded the file FP9_plugin_beta_101806.tar.gz and extracted the libflashplayer.so file from that and simply copied it to the various folders as root.  It worked for me so perhaps it will for you too.

---

### Post by FusionXN1 on 2006-11-15
I just did mine and im a noob to ubuntu :) I installed flash then what i did was download the new one from adobe, extract to my desktop opened a terminal and did:

cd ./Desktop/flash-player-plugin-9.0.21.55
sudo mv libflashplayer.so /usr/lib/firefox/plugins

Opened firefox and there she is, right click on a flash file and it says About Flash Player 9...

Hope this helps - im real happy I managed to do it by myself but just thought I would let you know how I managed to do it. **I did it with firefox not running while i moved the file**.

Let me know if it helps :)

**EDIT:** This is the version I got: [CLICKY](http://download.macromedia.com/pub/labs/flashplayer9_update/FP9_plugin_beta_101806.tar.gz)

---

### Post by dheerajsp on 2006-11-15
this worked very well for me...

open:
[http://labs.adobe.com/downloads/flashplayer9.html](http://labs.adobe.com/downloads/flashplayer9.html)

download Download Installer for Linux (GZ, 2.48 MB)

tar zxvf <file>

cd flash-player-plugin-9.0.21.55/

cp libflashplayer.so ~/.mozilla/plugins

open: [http://www.adobe.com/products/flash/about/](http://www.adobe.com/products/flash/about/)

flash on the lower right should say version 9,0,21,55 installed

---

### Post by araz on 2006-11-15
Another way to [install]("http://ubuntuforums.org/showthread.php?t=279990&highlight=flash+9") flash 9. It helped me a lot(its easier:-D ).

---

### Post by fettuohi on 2006-11-15
about:plugins does show that the flash-plugin is installed and it is flash 9 d55.

Regards

André

---

### Post by fettuohi on 2006-11-15
> **ajgreeny said:**
> Does your *firefox, about:plugins* show the plugin as installed?  I tried doing it myself and got a problem with either the version still showing as 7, not 9, or not showing at all.  I ended up by backing up the old versions of *libflashplayer.so* as *libflashplayer.so~* and then copying the new version 9 of *libflashplayer.so* into the several places where it was before.  On my system there are many links to the actual file *libflashplayer.so* (in /usr.lib/flashplugin-nonfree) and I had to change all of them for some reason to the actual file rather than the links they were before in order to get it to work as v9.  Very strange, but it works great now.

Try downloading the flash player 9 plugin installer from adobe, direct.  I downloaded the file FP9_plugin_beta_101806.tar.gz and extracted the libflashplayer.so file from that and simply copied it to the various folders as root.  It worked for me so perhaps it will for you too.

I already did that and it didn't work.

Regards

André

---

### Post by fettuohi on 2006-11-15
Any other suggestions?

Regards

André

---

### Post by fettuohi on 2006-11-17
Solved: Theproblem was Adblock Plus and Adblock: Filterset.G :). Thanks to all the suggestions. Problem solved :).

Regards

André

---

