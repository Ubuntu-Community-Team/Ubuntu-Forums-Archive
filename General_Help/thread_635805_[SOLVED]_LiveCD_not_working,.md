---
title: "[SOLVED] LiveCD not working,"
date: 2007-12-09
forum: General Help
---

### Post by sphere9 on 2007-12-09
i posted this over in absolute beginner talk but couldn't find any help,

here is my problem,

"I've tried downloading the LiveCD three times, once through the torrent and twice off the website, burnt them correctly verified .etc (I also requested 2CDs from ShipIt and both are giving me the same result)

they all seem to work fine until i try to run the Live environment in which i get the usual Ubuntu boot screen with the orange bar, once loaded the screen goes black and a screwed up looking block of green (think MissingNo from pokemon or Nine Inch Nail's Year Zero websites) and it just... hangs there.

By holding in the power button on my PC it brings me to the Ubuntu desktop.. in some bizarre resolution that the resolution settings will not let me change.

I have also tried running Ubuntu as a live USB and recieve the same problem, however after awhile i get a screen with an error something along the lines of "The Display Server has been shutdown 6 times in 90 seconds".

Please help me

Update:

Forgot to post my system specs;

Intel Pentium 4 CPU 3.00GHZ
895MB RAM
NVIDIA GeForce FX 5200"


P.S i am trying to run the Live environment, not install it.

thanks! :)

---

### Post by overdrank on 2007-12-09
> **sphere9 said:**
> i posted this over in absolute beginner talk but couldn't find any help,

here is my problem,

"I've tried downloading the LiveCD three times, once through the torrent and twice off the website, burnt them correctly verified .etc (I also requested 2CDs from ShipIt and both are giving me the same result)

they all seem to work fine until i try to run the Live environment in which i get the usual Ubuntu boot screen with the orange bar, once loaded the screen goes black and a screwed up looking block of green (think MissingNo from pokemon or Nine Inch Nail's Year Zero websites) and it just... hangs there.

By holding in the power button on my PC it brings me to the Ubuntu desktop.. in some bizarre resolution that the resolution settings will not let me change.

I have also tried running Ubuntu as a live USB and recieve the same problem, however after awhile i get a screen with an error something along the lines of "The Display Server has been shutdown 6 times in 90 seconds".

Please help me

Update:

Forgot to post my system specs;

Intel Pentium 4 CPU 3.00GHZ
895MB RAM
NVIDIA GeForce FX 5200"


P.S i am trying to run the Live environment, not install it.

thanks! :)

Hi, you can try when you reach the screen to start/install ubuntu press F6 and edit the kernel line and remove quiet splash and vga=771 before the -- then press enter. You may try vga=775 instead of 771 also. Hope this helps and good luck.

---

### Post by sphere9 on 2007-12-09
> **overdrank said:**
> Hi, you can try when you reach the screen to start/install ubuntu press F6 and edit the kernel line and remove quiet splash and vga=771 before the -- then press enter. You may try vga=775 instead of 771 also. Hope this helps and good luck.

Uhm, sorry i'm a noob with these things and that sadly made no sense to me :(

---

### Post by amckenzie on 2007-12-11
> **sphere9 said:**
> Uhm, sorry i'm a noob with these things and that sadly made no sense to me :(

While I'm not sure whether overdrank's advice will fix the problem (I'm working on the same issue myself), I can explain what he meant.

When you boot from the LiveCD, you'll get to a screen with a lot of options (Boot/install Ubunut, boot/install in safe graphics mode, etc.).

At that screen, if you press the F6 key, you'll get the option to edit the boot parameters -- the information the LiveCD uses to figure out how to boot.  On that line, overdrank recommends erasing the bits that say "quiet splash" and "vga=771".  (As a side note, my system doesn't seem to have the "vga=771" section.)  You can also try changing the "771" to "775". 

Let us know if it works!

---

### Post by sphere9 on 2007-12-12
thanks for the help, i couldn't find the VGA line but I removed the quiet splash and it seemed to work fine!

thanks :D

---

