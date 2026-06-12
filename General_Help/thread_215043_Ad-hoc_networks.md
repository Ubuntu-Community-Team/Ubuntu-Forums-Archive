---
title: "Ad-hoc networks"
date: 2006-07-13
forum: General Help
---

### Post by compwiz18 on 2006-07-13
I'm having trouble connecting to Windows ad-hoc networks using ndiswrapper and network manager (nm-applet)...Any ideas as to why?

If need be, I can post the iwlist and iwconfig and all that other useful junk, but I'm using Windows now so I can connect to the dumb thing...

Thanks in advance.

---

### Post by compwiz18 on 2006-07-14
Well, it worked once.  And then I rebooted. Guess what happened...

Any ideas?

---

### Post by compwiz18 on 2006-07-15
I'VE GOT IT!!!

For search purposes: if you run **iwconfig eth1 essid "PUT_YOUR_ESSID_HERE" mode ad-hoc** before you connect USING WIFI-RADAR (install with: **sudo apt-get install wifi-radar**, then run **sudo wifi-radar**) and you can connect to your ad-hoc network :D  This might work with network manager, I haven't tried it.

---

