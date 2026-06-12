---
title: "Simple but annoying problem when scrolling in browsers"
date: 2007-03-03
forum: General Help
---

### Post by RUGUNIT on 2007-03-03
When i am in a browser and scrolling up and down the page, it goes incredibly slow. This never happened when i first installed it two days ago, but now its just annoying to use. Ive actually been rebooting and using XP just to browse the internet because of this. It happens really bad in firefox and better but still bad in opera.

Anyone else had this problem or know of any programs or anything that may have caused such a thing? I installed the new drivers for my graphics card, which could be the culprit, but thats all i could think of. I just installed Ubuntu two days ago and installed a whole bunch of stuff at the same time, so it could be anything.

Thanks for any help.

---

### Post by tgalati4 on 2007-03-03
Less than 256 MB of RAM?

---

### Post by RUGUNIT on 2007-03-03
256+512

768mb RAM

Pentium 4

---

### Post by tgalati4 on 2007-03-03
I experienced slow scrolling on an HP Omnibook:

166 MHz, Pentium MMX, 64 MB.  Fluxbuntu was dreadfully slow.  Went to DSL.

Much better.

In a terminal:

top                          (control-C to exit)

to see if something is running at 100% CPU.  Sometimes scrolling problems is the result of a background process hogging the CPU.

Could be the slocate database updating after loading a bunch of stuff.  This is normal.  Let the process run to completion.  Shutting it down means it just restarts everytime because it never finishes.  One of the annoyances of Linux.  Thankfully it doesn't run very often.

---

### Post by RUGUNIT on 2007-03-03
Im on broadband: Time Warner Cable, so speed isnt the issue.

When i use top in terminal and scroll this browser, xorg takes up almost all of the CPU usage...it hit 93% at the highest that i saw...any fix for this? Is this normal?? It happens when i drag and drop anything or move anything open around by dragging it...

Thanks

---

### Post by tgalati4 on 2007-03-04
My Xorg uses 24% when moving transparent terminals around the desktop.  This is on a 500 MHz, PIII laptop.  It uses 4 to 5% otherwise.  On  your machine it should be much less because of the processor speed difference.

What is your graphics card?  What video modules are loaded for it? (lsmod)

---

### Post by kerry_s on 2007-03-04
Sounds like your using ATI?

---

### Post by RUGUNIT on 2007-03-04
Im using an older nvidia gforce2. I have the legacy drivers up to date. However, i was having issues previous to this where i couldnt even get the x server to start up. I had to go into recovery mode and switch things around with my graphics so that could be the culprit. I just dont know how to go about fixing it.

Also im not using transparent windows or anything like that, no 3d stuff either, just a straight up browser.

Thanks

---

### Post by kerry_s on 2007-03-04
Run> sudo nvidia-xconfig
then reboot

---

### Post by RUGUNIT on 2007-03-04
Alright that worked great. Thanks everyone who helped.

---

### Post by kerry_s on 2007-03-04
Just so you know in case you want to make changes, nvidia has a gui for that.
gksu nvidia-settings.

---

