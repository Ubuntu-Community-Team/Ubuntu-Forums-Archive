---
title: "Synaptics TouchPad gesture suite drivers"
date: 2013-12-17
forum: General Help
---

### Post by LifeEnemy on 2013-12-17
Hi all,

I recently bought an Acer Aspire V5-572G-6679 with a nifty multi-touch pad and neat gesture software. It worked in windows 8, but I got rid of that and put on 12.04. However, I can't figure out how to make the advanced features work. The synaptics website has a page on their [linux driver]("http://www.synaptics.com/solutions/technology/touchpad-linux"), but doesn't seem to provide it anywhere. I found a page they linked pointing to 'independent developers' who have made a driver, but I can't make heads or tails of the site. How would I use this to install the necessary drivers?

link: [http://cgit.freedesktop.org/xorg/driver/xf86-input-synaptics/](http://cgit.freedesktop.org/xorg/driver/xf86-input-synaptics/)

I downloaded the most recent (?) zip file in the second group, but the readme file was over my head ?:(

Thanks in advance!

---

### Post by LifeEnemy on 2013-12-17
I tried the fix described [here]("https://bugs.launchpad.net/ubuntu/+source/xf86-input-multitouch/+bug/308191?comments=all") in comment 115 and 116, but the deb file failed to install. The ppa mentioned a few comments later (utouch) also failed to install anything.

Also attempted a glidepoint driver (probably wrong, [source]("https://bugs.launchpad.net/ubuntu/+source/linux/+bug/606238/comments/144")), but it didn't seem to do anything and I was unable to figure out how to configure it.

Found some documentation on X.org. I ran "xinput list-props 13" (the device ID of the trackpad), it seems there are some options for enabling some of the fancier gestures (circular scrolling, enabling middle click emulation, perhaps even shrinking the pad area slightly so I can use the 'buttons' without moving the cursor about). However, I'm unsure how to configure these options exactly. Do I have to create a xorg.conf file, or can I simply change a few values from the command line?

Still unsure how to enable pinch zooming or a three-finger swipe gesture. Suggestions?

---

### Post by LifeEnemy on 2013-12-18
Well, I figured out how to use xinput to change the settings and set 'circular scrolling' to 1(on?), but it still doesn't work. Now I'm entirely confused :confused:

---

