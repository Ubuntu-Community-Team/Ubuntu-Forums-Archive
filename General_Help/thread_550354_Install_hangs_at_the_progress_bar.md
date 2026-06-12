---
title: "Install hangs at the progress bar"
date: 2007-09-13
forum: General Help
---

### Post by bigfinger76 on 2007-09-13
I checked all relevant threads before posting, but none are specific to my problem. Sorry...

I'm trying to install from LiveCD, and I can get to the Ubuntu splash/progress bar screen if I change settings from VGA to any of the other resolution options (if I leave it on VGA, I get nothing but a blank screen). The attractive splash screen shows no progress, and the cdrom drive ceases activity shortly thereafter.

Specs:
AMD Athlon 64 X2 4000+ CPU
ASUS M2A-VM HDMI mobo
1 gig of RAM
Seagate 80GB SATA HD
HP DVD640 DVD-ROM
Nvidia GeForce 7200GS GPU

Any help you folks could offer would be greatly appreciated.

---

### Post by thedarkwinter on 2007-09-14
Hi

Have you tried booting in safe setttings mode (the second option). There is a problem with the nvidia driver when booting of the CD (its fine once its installed). Safe settings uses the vesa driver rather than trying to detect your video board.

Cheers,
tdw

---

### Post by bigfinger76 on 2007-09-14
Thanks for the response.

I have tried "Safe Graphics Mode", but it still freezes up. Is there a way to manually force it to load the vesa driver? I've seen mention of it, but I can't get to a command prompt.

*edit

All guides I read assume I can easily get to a prompt. How do I do this?

---

### Post by bigfinger76 on 2007-09-15
Got it booted with the alternate disc. How do I permanently change my resolution?

---

### Post by vesper8 on 2007-09-25
what do you mean you got it to work with the alternate disc?

 I have the same Mobo as you and apparently the same problems! And I'm still looking for a solution here... please let me know how you got it to install on the M2A-VM ?

thanks!

---

