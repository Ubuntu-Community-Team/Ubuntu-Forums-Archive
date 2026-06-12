---
title: "Resolution refresh rate"
date: 2007-05-08
forum: General Help
---

### Post by Soad123 on 2007-05-08
My NVIDIA G FORCE 2MX440 will only show 50 or 55hz at 1280 x 1024 am using the restricted drivers that was in the system in 7.04

---

### Post by m.musashi on 2007-05-08
What exactly is your question? I have a different card but mine did the same thing. I was using feisty beta and after trying several fixes and only making things worse I did a clean install. After that all was fine. However, I can't see one bit of difference in the refresh rates. Maybe because I don't play games or something. If it's working fine I would leave it.

Is this something you want to fix? If so, we'll need some more info such as what have you tried so far and is this an upgrade or clean install.

This is a command to reconfigure everything but given my fairly bad luck with it (things are usually worse and not better) I'm reluctant to suggest you try it. Let's try a few other things first. To begin with, what is your goal?

---

### Post by Soad123 on 2007-05-08
To change to a higher refresh rate like I can in Windows or Open Suse 10.2 I am running at 75hz

---

### Post by m.musashi on 2007-05-08
Sounds like the same thing I dealt with not too long ago. In my case the fix ended up being a clean install. If you are not up for that route, take a look at the info [here](https://help.ubuntu.com/community/FixVideoResolutionHowto). There is some info on running the auto detect script again and such. I would not try that as your first fix. It may work great but if you don't know how to answer the questions for your hardware things may end up worse. Instead, take a look at the manual edits of the xorg.conf file. At least those are easy to undo if they don't work. Be sure to make a backup and know how to replace it from a terminal in case you break X and can't log into a gui desktop.

I'm off to dream land. I'll check in tomorrow and see if you have any luck.

EDIT: One more thing. You might also check [here](https://help.ubuntu.com/community/DebuggingXAutoconfiguration). There is some info on a different approach to reconfiguring X. Specifically
```
sudo mv /etc/X11/xorg.conf /etc/X11/xorg.conf.orig
restart X
```
I've never tried that so I can't endorse it but it sounds like an easy solution.

---

### Post by m.musashi on 2007-05-08
Okay, for what it's worth, I gave this a try myself. I just noticed that my own computer has reverted to the 50 or 55 Hz options even though it was 60 and 75 before. I really don't know what's up with that.

Anyway, the commands I copied from that link were not correct. I edited the above but I can't find any such "restart" option. Ctrl-alt-backspace works fine though. After moving the xorg.conf file and restarting everything worked as it should. I had a 75 Hz refresh rate again and it stayed after a full reboot. However, it did not rebuild the xorg.conf file and I was surprised to find that it worked without it. Of course, without it, it did not load the nvidia driver so I was unable to use beryl.

So, basically, I'd say that this fix works in that you should get a better refresh rate but will lose your nviida driver. I'll have to look into this some more and see what is going on. I'm thinking now that it might be related to the nvidia card settings.

---

