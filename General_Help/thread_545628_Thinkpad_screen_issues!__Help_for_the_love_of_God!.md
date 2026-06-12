---
title: "Thinkpad screen issues!  Help for the love of God!  (with pictures!)"
date: 2007-09-07
forum: General Help
---

### Post by theuberpig on 2007-09-07
Hey.

So I finally got Ubuntu on my new Thinkpad, running Gutsy Gibbon Tribe 5.  Everything was going along swimmingly until I rebooted after installing all the updates...  Now the boot process looks OK until I get to the login screen, when the graphics flip out.  Totally.

Please, if anyone has a fix for this, let me know.  Here are the stats:

Lenovo/IBM Thinkpad T61
Core 2 Duo 2.0 ghz
2 gb RAM
Nvidia Quadro NVS140m graphics

...And here's what's going on.

[http://i98.photobucket.com/albums/l250/theuberpig/00001.jpg]("http://i98.photobucket.com/albums/l250/theuberpig/00001.jpg")

Also, I'm a total linux noob.  So if any directions could be rather step-by-step, that would be LOVELY.  Sorry!

Any help is appreciated!  Thanks in advance!

edit: image is now a link

---

### Post by rivalarrival on 2007-09-07
Reboot. At grub menu, select "recovery mode" Login.

At the command line, type:

```
sudo dpkg-reconfigure xserver-xorg
```

and follow the steps.

It looks like it has gotten into a resolution that your monitor doesn't support, and that command should let you fix the problem.

When you're done, reboot and everything should be good to go.

---

### Post by RedSquirrel on 2007-09-07
> **theuberpig said:**
> edit: probably should have resized that.  sorry!

and/or you could attach it... ;)

---

### Post by theuberpig on 2007-09-07
OK.  I tried that first idea...  Rebooted and all I got was a black screen.  Gave up and reinstalled.  Now I'm up and running again.  Just like last time, it allowed me to reboot and everything looks OK.  Too afraid to install the updates and reboot again lest I get the same issue.  Is there some way I could prevent this from happening again?  Could it just be the update that screwed me the first time?

Thanks,
Robert

---

