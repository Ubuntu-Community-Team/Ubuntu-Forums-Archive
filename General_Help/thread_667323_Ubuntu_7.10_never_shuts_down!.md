---
title: "Ubuntu 7.10 never shuts down!"
date: 2008-01-14
forum: General Help
---

### Post by th_agorastos on 2008-01-14
Hi, I've installed Ubuntu 7.10 a long time ago. Everytime I shutdown the machine ubuntu shows the following messages (see attached screenshot) and does nothing at all (I tried leaving the machine untouched for about 10min and still nothing). The only way to shut down my PC is to use the power button.

[[IMG]http://www.imageshack.gr/files/f27u8kcits3laaaelq3t.jpg[/IMG]](http://www.imageshack.gr/view.php?file=f27u8kcits3laaaelq3t.jpg)

The real problem comes when I'm connected to my box through ssh and I want to perform a restart (it never works!)

Any clues?

---

### Post by ugm6hr on 2008-01-14
My laptop would go to a blank screen and hang forever when shutting down, but occasionally show similar messages first.

I discovered the problem was the "Experimental Intel Video Driver" - do you have an on-board Intel video chipset?  If so, try the original driver (I used i810).  I had to set it manually in xorg.conf though (the GUI didn't work).

---

### Post by th_agorastos on 2008-01-14
I have a NVIDIA FX5200 AGP video card.

Everything worked ok on the older version of Ubuntu.

The messages say something about Network Manager and eth0 interface so I speculate this should have something to do with the network (?)

---

### Post by th_agorastos on 2008-01-26
Any ideas anyone? I'd appreciate your help!

---

### Post by aliencam on 2008-01-26
same thing happens to my desktop, and that is a radeon 9800 pro (neither nvidia or intel)

---

### Post by eapache on 2008-01-26
I get the same messages, but then it shuts down fine. I don't think the message and the error are related. Try removing splash and quiet from your grub options, and see if it gives a more precise error before hanging.

---

