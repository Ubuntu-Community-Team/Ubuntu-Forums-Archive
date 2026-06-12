---
title: "Strange Crashing Problem"
date: 2007-09-04
forum: General Help
---

### Post by waveslider on 2007-09-04
I have just begun to experience strange crashes in Ubuntu in the last two days. I've never had Ubuntu crash on me like this before.

Everything will be going smoothly, then suddenly the screen freezes without warning; the mouse won't react, nor will the keyboard. Pressing CTRL-ALT-BACKSPACE has no effect whatsoever.

Around the time this started I installed an HTML validator extension from the W3, and a deb package that configures NVidia drivers that I read about on Digg.com. The other software I'm running that I suspect as culprits is: Google Desktop, Compiz (with Emerald decorator), and screenlets.

Which log file can I read to try to sort this out, and what should I be looking for? I tried reading /var/log/syslog, but I couldn't make any sense of it.

Thanks!

P.S. How do I uninstall software (this NVidia driver manager) that I've downloaded and installed as a .deb file?

---

### Post by bogdan_5844 on 2007-09-04
Try uninstalling the nvidia software by going in synaptic and searching for the filename of the .deb file(that's how i do :-P )and then try running Ubuntu without compiz,see if that solves the problem

---

### Post by waveslider on 2007-09-04
Hi,

Thanks man. I actually did that, but now GDM won't work because of a problem with Xorg. I backed up my original (totally working) xorg.conf file before I made any changes last week, but it no longer works.

I uninstalled that questionable Nvidia .deb from Synaptic, then unenabled and then reenabled the Nvidia driver through the Restricted Driver manager program, but I still can't get Xserver/Gnome to work.

I've tried dpkg-reconfigure xserver-xorg twice now, but it's not working. I'm kind of freaking out because I have a ton of work to do. 

Does anyone know what I can do to restore my system to a working state?

Thanks everyone!

---

### Post by bogdan_5844 on 2007-09-04
well...i don't really know,but if i were you,i'll boot from the live cd,save my data somewhere and reinstall everything...i know,i know,but i did this thing like 5 times in one day,so it isn't a big deal if you have an USB HDD or a USB Stick...anyway if you don't want that try installing kubuntu-desktop/xubuntu-desktop see if works
other than that...i really have no idea :confused:

P.S.Sorry,but I'm a newbie :-P so i don't really know much

---

