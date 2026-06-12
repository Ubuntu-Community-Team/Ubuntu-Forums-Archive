---
title: "Add TV-out to xorg.xonf? (nVidia)"
date: 2005-10-30
forum: General Help
---

### Post by pickarooney on 2005-10-30
I've been messing with different configs but can't quite get TV-out to work on my new Ubuntu installation with my xorg.conf file. 
The physical connections are fine, as this worked with my previous Mandrake installation, but I'm missing something in xorg.conf.
Can anyone tell me what I need to add here?

Thanks,
P

---

### Post by BigMurph on 2005-10-30
Hey,

First off comment out the "dri" and "GLcore" modules in the modules section.

Next, you need to decide if you want your TV to be a clone of what you see on your monitor, or a second seperate X screen. Either way, under device you should add

Option    TwinView "on"

If you want clone, then put

Option    TwinViewOrientation "Clone"
(I'm not sure if this is the proper option name, check the NVidia documentation)

There are a few other options you can get from the documentation. It looks like you already have a handle on this by the looks of your Mandrake file.

If you want two seperate X screens you need to set up another device. I've attached my dual X-screen config.

Hope this helps.
Murph

---

### Post by pickarooney on 2005-10-30
Thanks for the quick answer, BigMurph :)
Unfortunately, X won't start with those changes, I get a big list of errors and warnings that scrolls off the screen and then xinit fails.
Rebooting now with your TV.txt config...

---

### Post by pickarooney on 2005-10-30
OK, got it, my device names weren't matching, got it all sorted now (w00t!).
Cheers,
P

---

### Post by graabein on 2005-11-02
How about posting the fixed xorg.conf? ;)

---

### Post by pickarooney on 2005-11-02
of course! :)

---

