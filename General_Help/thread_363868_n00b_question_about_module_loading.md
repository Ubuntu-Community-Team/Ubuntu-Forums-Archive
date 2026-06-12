---
title: "n00b question about module loading"
date: 2007-02-17
forum: General Help
---

### Post by pollyp on 2007-02-17
Hi,

I am new to Ubuntu and have a question about how to configure module loading.

I have a HD TV card, the HD-3000 sold by pcHDTV. Out of the box, Ubuntu loads the video4linux modules for the card. I prefer to use the dvb drivers instead. 

I created an init script to unload the v4l drivers and load the dvb drivers. This works great, but I'd like to figure out how to get the card associated with the right drivers in the first place. I would have thought I'd find the drivers getting loaded in one of my /etc/modprobe.d scripts, but it's not there.  Can anyone give me some hints about how to do that? 

Many thanks ...

Polly

---

### Post by lloyd_b on 2007-02-18
Take a look in the file "/etc/modules", and see if the v4l driver is specified in there.  If so, change it to the dvb driver.

Lloyd B.

---

### Post by pollyp on 2007-02-20
Thanks for your reply. I did check my /etc/modules, and it didn't have any references to v4l in it. Any other ideas about where the v4l drivers are getting associated with my card?

TIA,

Polly

---

### Post by Maestro23 on 2007-02-20
> **pollyp said:**
> Thanks for your reply. I did check my /etc/modules, and it didn't have any references to v4l in it. Any other ideas about where the v4l drivers are getting associated with my card?

TIA,

Polly

Do a:

locate v4l

---

### Post by az on 2007-02-20
> **pollyp said:**
>  This works great, but I'd like to figure out how to get the card associated with the right drivers in the first place. I would have thought I'd find the drivers getting loaded in one of my /etc/modprobe.d scripts, but it's not there.  Can anyone give me some hints about how to do that? 

Many thanks ...

Polly

You should do two or three things.

1.  Blacklist the modules you don't want to load.  Look in /etc/modprobe.d and blacklist the v4l module.

2.  Load your modules at boot.  Put them in /etc/modules, one per line.

3.  File a bug report.  Your device should work out-of-the box.  PLease file a bug report so that it will eventually work for everybody.

---

### Post by pollyp on 2007-02-22
Making the modifications to the modprobe.d directory worked. - thanks! I  did do one thing different -- my HD-3000 card was not recognized, so I added a line to the options file in modprobe.d to give the cx88xx module the "card=22" parameter. 

I'm not inclined to file a bug report on this, though. It's not that the v4l drivers are broken; it's just that I intend on installing mythtv, and the wiki I read said that mythtv ran better with the dvb modules than the v4l modules. That's why I was switching.

Again, thank for your help.

---

