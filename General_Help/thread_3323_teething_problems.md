---
title: "teething problems"
date: 2004-11-05
forum: General Help
---

### Post by andy_sp1ke on 2004-11-05
Well I have been enjoying myself with Ubuntu in the last 24 hours, only a few little teething problems. I cant seem to get MPlayer to install the gui. I run ./configure --enable-gui and goes fairly well up to a point. Then it halts saying i need to install PNG support which i am failry sure i have done by install libpng-1.2.7 , libpng-1.2.8beta3 (libpng-dev package) and also Zlib. they all seemed to configure properly, For each I ran the makefile.linux script, make, make install. But still MPlayer wont install the GUI!! Anyone got any thoughts?!?! Also I want to put links to certain directories on the panel. I can make the icons work on the desktop but as soon as i move them to the panel they die which is annoying because I want to clear up the desktop and use custom icons for HOME, my Removeable drive etc. !

One final question..what is the point in the ToTem player shipped with the distro?! It wont play anything!!!! I have copied the codecs from the mplayer site (the package called All) to /usr/local/lib/codecs and in totem they appear in the directory that opens when you click add propetary plugins but it still plays nothing. where can i get the correct plugins?

Cheers

Andy

---

### Post by moon2js on 2004-11-05
I had the exact same problems.

For gmplayer, I installed libpng12-0 and it works fine.

For totem, I have no idea. After Ubuntu installation, it was completely useless. I've tried to fiddle with codecs and whatnot, but it still gives the "unknown" error, and I couldn't get it to play anything.

I eventually installed totem-xine (uninstalling the original totem-gstreamer in the process), and to my surprise, it seems to be working. I'd like to hear how other people got it working.

---

