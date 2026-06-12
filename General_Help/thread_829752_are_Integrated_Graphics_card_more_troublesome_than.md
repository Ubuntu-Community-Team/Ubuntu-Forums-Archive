---
title: "are Integrated Graphics card more troublesome than separate graphic card?"
date: 2008-06-15
forum: General Help
---

### Post by richardmems on 2008-06-15
I just installed ubuntu 8.04 on new pc. everything is ok except graphical interface is coming badly.

the graphic unit i am using is integrated on MSI P4M900M3 motherboard.

is it relatively easy to install separate graphic card than integrated ones?

regards
richard

---

### Post by Pjotr123 on 2008-06-15
You probably have a VIA graphics chipset on your motherboard. VIA and SIS are often troublesome in Linux. 

You can add a separate video card easily. Choose Nvidia, because ATI doesn't have very good Linux drivers, and Nvidia has excellent drivers. A cheap Nvidia card is good enough; Ubuntu doesn't need powerful hardware.

Remember to disable the video chipset on the motherboard in the BIOS, after you've plugged in the separate video card. That prevents trouble: Ubuntu doesn't like more than one active video card.

After plugging in the new card, do this first:
[http://ubuntutip.googlepages.com/nodisplay](http://ubuntutip.googlepages.com/nodisplay)

and then this:
[http://ubuntutip.googlepages.com/thefirstthingstodo](http://ubuntutip.googlepages.com/thefirstthingstodo)
(number 2 )

and lastly this:
[http://ubuntutip.googlepages.com/bugsinubuntu](http://ubuntutip.googlepages.com/bugsinubuntu)
(number 2 )

That'll do the job nicely.  :-)

Greeting, Pjotr.

---

### Post by richardmems on 2008-06-15
Dear all

Yes, my onboard graphic chip set is by VIA. is there other way to install it's linux driver? pls help....

thks...

Richard

---

