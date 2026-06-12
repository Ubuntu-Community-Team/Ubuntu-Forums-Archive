---
title: "Need help on Twinview for HP Pavilion dv2000"
date: 2006-12-21
forum: General Help
---

### Post by sarc on 2006-12-21
Hi,

I have an external LCD monitor and I want to extend my desktop to it.  It has nvidia GeForce 7200.

The last time I tried to install an nvidia enhancement it took me three days to get x11 to work again.

So before I try this HOWTO:

[http://www.ublug.org/ubuntu/twinview/twinview-howto-breezy.html](http://www.ublug.org/ubuntu/twinview/twinview-howto-breezy.html)

I would like to know it it's likely to work!  Or nuke my x11 into oblivion again.

Ideally, I would like to control the external monitor on/off and resolution through GUI i.e. to hook up to projectors for presentations while keeping my on desktop running; and to have a bigger virtual desktop while I work.

p.s. do I understand correctly that there is no GUI way of controlling multiple monitors in Gnome? :( 

Thanks!

---

### Post by sarc on 2006-12-24
10 views and no replies?  Come on it's Christmas!  Have some heart!

p.s. Sorry I had too many margaritas when I wrote the post... I meant Xwindows, not x11...

---

### Post by bodhi.zazen on 2006-12-24
It should work.

Try it and post if you have specific questions or problems.

[How to twinview](http://www.ubuntuforums.org/showthread.php?t=221174)

FYI the latest nvidia driver has a GUI for configuration.

See here for latest nvidia: [http://albertomilone.com/nvidia_scripts1.html](http://albertomilone.com/nvidia_scripts1.html)

Use the latest, bleeding edge driver .....

Also, you sound as if you have not backed up xorg.conf.

Before you start,```
sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf.bak
```

To restore, ```
sudo cp /etc/X11/xorg.conf.bak /etc/X11/xorg.conf
```

HTH

---

### Post by sarc on 2006-12-25
You mean nvidiaconf (or something like that)?  I tried it..
Last time I installed a Invidia scripts I had to reinstall Edgy... can't afford to take chances any more... no safe 100% foolproof way = I'm sticking with one monitor

---

### Post by spockrock on 2006-12-25
actually there is, run nvidia-settings, as long as you are not running xgl, but aiglx, or neither, you can from there manipulate your twinview settings.  But you need to have the nvidia-glx drivers installed. enjoy.

---

### Post by sarc on 2006-12-26
So there is!  Nice surprise!

Te GUI only shows ine monitor at a time.  If the external monotor is connected to the VGA port, it only shows that one.  if no external monitor, it only shows the notebook's LCD panel.  I suppose its a xorg.conf business to tell xwindows that there are 2 monitors, then use nvidia-settings to switch to one, the other, or both... but how?  Previous posts in this forum are too risky for me as indicated...

---

### Post by spockrock on 2006-12-26
have you clicked the configure, or detect buttons where you are shown the monitor layouts??
btw setting up twinview in xorg.conf isnt that difficult.....I really suggest you give it a try...

---

