---
title: "graphics not working right!!"
date: 2008-04-08
forum: General Help
---

### Post by doctorgreg on 2008-04-08
My graphics are running pretty sketchy when I am just using metacity.  My compiz won't even work anymore.  While on metacity there are a few glitch marks on my gnome panel and everythings is just slower than it used to be.  Metacity and Compiz ran smooth before.  All this started happening after I had used an external LCD monitor.  So I don't know what the heck happened.  Something must have changed.  Please help.

---

### Post by ryanhaigh on 2008-04-09
Is it possible that you have upgraded your kernel and the display drivers are incompatible?

---

### Post by forrestcupp on 2008-04-09
You didn't give very much info.  What do you mean by "external LCD monitor"?  Are you using a laptop, and when you plugged a monitor into it, it became slow with glitches?  What kind of video card/chipset do you have?  What drivers were you using for it?

---

### Post by doctorgreg on 2008-04-09
A 19" flat panel monitor.  Yes  I am using a laptop.  I have the ATI Radeon Xpress 200M, AMD 64 Athlon, 1GB ram/1GB swap.  I am using the FGLRX driver.  What happened is I have had gutsy with compiz running very smooth for like 5 months now and last week I was using that lcd tv as an external monitor for a bit.  Everything was still working just great while using the external.  But after i was done with it everything went to hell.  Seems like it might be something wth the screen settings.  Who knows.

---

### Post by doctorgreg on 2008-04-09
I have no idea it it has anything to do with the kernal or not.

---

### Post by ryanhaigh on 2008-04-10
You may want to check whether the fglrx driver is even being used anymore, compiz not working and metacity being slow might indicate the vesa driver is being used. Check you xorg.conf file and xorg logs. If your kernel has been upgraded you will have another option at the grub menu, depending on how you installed the driver for your ati card using the older kernel may get things going again.

disclaimer: not an ati user

---

