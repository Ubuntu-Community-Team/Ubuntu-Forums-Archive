---
title: "Problems with adobe flash &amp; 12.04"
date: 2014-08-11
forum: General Help
---

### Post by sports fan Matt on 2014-08-11
Whenever I try to play anything with flash such as [http://www.mykzradio.com/](http://www.mykzradio.com/) always comes up with the flash player being not installed but it's working because I can view Youtube..etc.  (This only happens in Chromium, as FF is fine). Any ideas as to why this is occurring and a solution?  

Thanks.

---

### Post by Dennis N on 2014-08-12
Chromium, starting with version 34, now needs pepperflash-plugin to view flash video. Have you installed it? For 14.04, its in the Ubuntu repositories. For 12.04, you need to use a PPA:
[https://launchpad.net/~skunk/+archive/ubuntu/pepper-flash](https://launchpad.net/~skunk/+archive/ubuntu/pepper-flash)
Be sure to read the instructions there. A possible reason you can see some video on YouTube is because it's not flash video, its HTML5.

---

### Post by sports fan Matt on 2014-08-12
I did install it.  Youtube works fine but sites above do not still.  /etc/chromium-browser/default  . /usr/lib/pepflashplugin-installer/pepflashplayer.sh . How would this be with gksudo?

---

