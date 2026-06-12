---
title: "Slow Scrolling in Xubuntu Edgy Apps"
date: 2007-01-07
forum: General Help
---

### Post by Simplesoul on 2007-01-07
I have installed Xubuntu Edgy on an old Sony Vaio N505x and it runs really well except for a couple of things. In some apps scrolling a page is sometimes really, really slow - I mean like 1 pixel at a time. This appears to be in both ABI word and Openoffice word. It also smears the bottom few characters on the page as it tries to scroll down. The other thing is moving windows around the desktop seems to refresh really slowly. I have run the usual dpkg-reconfigure -phigh xserver-xorg and its giving me 1024x768 at 75hz which seems reasonable. Anyone got any ideas?

---

### Post by justifier on 2007-01-07
this could be because those two programs are orignaly written for GNOME, KDE, not 100% sure on this tho so dont hold me to it. are there any native xfce office applications?

---

### Post by Simplesoul on 2007-01-07
The only one that is native appears to be mousepad and that does behave a bit better. But whats the point of making a desktop OS with the only Office Apps almost unusable? What do people use it for then? Just browsing? 

Anyway it's not just the office apps its the general refreshing of windows that is poor. At this rate I may have to sling a version of XP back on it with the graphics tweaked down just to be able to do usable word processing!

---

### Post by jhow on 2007-01-18
I have exactly the same problem but with all windows and scrolling any pages. In my case I'm pretty sure my onboard graphics have not been detected properly.

try 

sudo lspci -v 

and look at the results mine states my video card is unkown device

also start up system monitor and watch the cpu peak out by just moving a window around or scrolling cause all the graphics rendering is being done by your cpu.

solution: I dont know. I'm going to put an old nvidia FX5200 card in and see what happens

---

### Post by Duppy on 2007-01-20
Same with me, Ive installed it on a laptop and the firefox scrolling is slow and moving windows around makes the cpu peak. We need help here... anyone?

---

### Post by meb495 on 2007-01-21
I had the same problem upon upgrading.  Amazingly I just ran:

sudo dpkg-reconfigure xserver-xorg

And the problem was fixed after a restart!  I selected all the defaults in the reconfigure routine.  I'm using the VIA VT8237 chipset.

---

### Post by yogiman_uk on 2008-06-08
> **Simplesoul said:**
> I have installed Xubuntu Edgy on an old Sony Vaio N505x and it runs really well except for a couple of things. In some apps scrolling a page is sometimes really, really slow - I mean like 1 pixel at a time. This appears to be in both ABI word and Openoffice word. It also smears the bottom few characters on the page as it tries to scroll down. The other thing is moving windows around the desktop seems to refresh really slowly. I have run the usual dpkg-reconfigure -phigh xserver-xorg and its giving me 1024x768 at 75hz which seems reasonable. Anyone got any ideas?

Hi

A quick question, how did you get the Vaio to boot the cd correctly.

I have same laptop with external PCMCIA CDROM and my usual trick is to add this line to the boot options: ide1=0x186,0x386 nopcmcia acpi=off

However using this on Xubuntu achives nothing and the installer can not find the CD.

Any help you can offer would be great.

Thanks

Yogiman!

---

