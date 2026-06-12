---
title: "Gutsy Gibbon: network manager not working at all"
date: 2007-10-18
forum: General Help
---

### Post by jojohippo on 2007-10-18
Hello, I'm fairly new with Ubuntu so forgive me for being so stupid. I just installed gutsy gibbon on my laptop. With feisty, I used to have to select my wireless network from the network manager and I would be connected. In gutsy when i select the network manager i get a 'manual configuration'. I right click and go to network settings and there is no option for wireless like there used to be. All i see is 'wired connection' (is left on roaming mode) and 'modem connection'. I don't even connect to the network when i plug in my ethernet cable...

There are so many webpages and forum posts for ubuntu's networking, they've left me a bit lost. If someone can just point me to the right one for me I' d appreciate it.

My network settings screen looks like this but without the 'wireless connection' option [http://video.linux-noob.com/screenshots/ubuntu/7.04/post-1-1178099383.png](http://video.linux-noob.com/screenshots/ubuntu/7.04/post-1-1178099383.png)

---

### Post by jojohippo on 2007-10-19
Bump

---

### Post by handaxe on 2007-10-19
```
sudo lshw -C network
```

This should show if your wireless card is present / recognised.

If not, then you need to try and modprobe the correct driver - or search the forums to see if that driver has problems under Gutsy.

HA

---

