---
title: "ACPI Error"
date: 2015-05-22
forum: General Help
---

### Post by markymark64 on 2015-05-22
I have 15.0.4 installed. Was watching a video on youtube and my system suddenly locked up with some nasty grey lines forcing me to do a hard reboot. I did read some instructions here and I used the boot repair app to try and correct the problem. Following in a link that I was told to share on the forum. 

paste.ubuntu.com/11296238

Please let me know how to fix this. I just switched back to ubuntu because I was tired of manjaro and everything was fine for a day. 

Cheers,

Mark

---

### Post by tgalati4 on 2015-05-23
Well, I read through the boot repair record and I didn't see anything unusual, except that you have a lot of partitions and a mixture of Windows and Linux.

[http://paste.ubuntu.com/11296238/](http://paste.ubuntu.com/11296238/)

So, exactly how does boot repair be the solution to (what appears to be) a graphics card lockup during a video?

What were your experiences with Manjaro?  Did your graphics card work OK?  Could you watch youtube videos?

What is your graphics card?

```
lspci | grep VGA
```

Is the problem consistent?  Did the hard reset mess up your disk in such a way that it won't boot anymore?  How old is this computer?

---

### Post by dino99 on 2015-05-23
are your logs showing some usefull warnings/errors ?
run > sudo journalctl  to know; glance at the red lines, and possibly to some bright white lines too

---

### Post by markymark64 on 2015-05-23
You just asked me if this problem is consistent. Please reread the thread. I just installed ubuntu 15.0.4 a day and a half ago. So no, the problem isn't consistent.

As for my graphics card, I'll admit it's a dang cursed Nvidia card and we know they do not play nice with Ubuntu because they're in Microsoft's back pocket. 

As for the hard reset, umm, I had no other option. My desktop had changed to grey, crisscrossed lines. 

Also, since this was the first time happening on ubuntu since I reinstalled it I wasn't sure it was a graphics card problem. I was hoping it was something else.

Anyway, thanks for your comments. I'll go back and do more research.  My graphics card is an Nvidia GeForce 6150 SE nForce 430.

---

### Post by markymark64 on 2015-05-23
dino99, i have no idea what to look for. There are a lot of bright, white lines from the past few days and a few red lines. However, there were none, that I could see, that indicated this was a video card issue. From everything I've read around this web this is related to the grub. I was hoping this would be an easy fix but, if it's not, I'll either reinstall or go with another distro. This is one instance where I'm pretty sure my video card was not the issue.

---

### Post by Vladlenin5000 on 2015-05-23
> **markymark64 said:**
> This is one instance where I'm pretty sure my video card was not the issue.

I wouldn't be so sure...
Being used to Manjaro you probably expect Ubuntu to automatically install nvidia drivers but that isn't the case: By default Ubuntu runs the open source driver *nouveau* which, albeit supporting you card, might not be the best choice.

---

### Post by markymark64 on 2015-05-24
Vladlenin, yes, I believe you are correct. In fact, I think I remember that this was why I switched out from Ubuntu several years back. It would change my video drivers every time it did an update. I'm pretty sure I saw an amusing video of Linus Torvalis giving the finger to Nvidia. lol. After spending an hour reinstalling and then updating and rebooting I found myself back at the root again. I'm not sure if I want to pull down and install the correct drivers or simply try another distro. Anyway, thank you and everyone who responded to this thread. 

Cheers,

Mark

---

