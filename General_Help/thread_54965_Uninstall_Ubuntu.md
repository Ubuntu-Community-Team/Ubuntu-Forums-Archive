---
title: "Uninstall Ubuntu?"
date: 2005-08-06
forum: General Help
---

### Post by darundal on 2005-08-06
Hi, I am attempting to rid a computer of Ubuntu (usually superb, but with 166 mhz and 92 mb of RAM, not that great) and reinstall windows 95 (because it is the only OS I have craptacular enough to work decently on that hardware). Is there some way to format the hard drive within ubuntu, because windows has issues with the filesystem, It can't create a temporary directory it needs for install. Thanks (and I will continue to be an Ubuntu user, just not on that system).

---

### Post by jasmuz on 2005-08-07
Hold on, just before you completely change your mind about eliminating Ubuntu on it, did you try using it with Blackbox, Fluxbox or Openbox wich are very low resource sucking inviroments.

---

### Post by auburn on 2005-08-07
what jazmuz says. the default ubuntu window system (gnome) is about the most resource hogging desktop available in linux. 

I'm pretty sure I've gotten knoppix to run on a similar machine. At the prompt simply type:
knoppix desktop=fluxbox
(or xfce instead of fluxbox. Prettier, but slower.)

To format a drive in linux:
sudo cfdisk /dev/hda

Then, assuming this is the correct drive (stop if you have more than one drive...) Use the arrows to select "TYPE" and choose 0B or 0C. You'll see the list of options.

Then I think you use the arrows again to select "write". That's what actually starts the formatting.

---

