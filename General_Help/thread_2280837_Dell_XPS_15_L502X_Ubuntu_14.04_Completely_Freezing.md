---
title: "Dell XPS 15 L502X Ubuntu 14.04 Completely Freezing"
date: 2015-06-02
forum: General Help
---

### Post by Caleb_Jefferies on 2015-06-02
About twice every time I use my laptop I get a complete freeze.  The keyboard and the trackpad both freeze giving me no way of input.  I close the laptop which puts it into suspend mode.  I then open it and hope it doesn't happen again but I can't figure out why this would be happening.  But this started happening after I got my laptop to find my NVIDIA graphics card.  Before this my laptop had been using a small integrated graphics card.  The NVIDIA graphics card was there but the computer didn't know where it was or how to use it or something.  Anyhow I followed these instructions to get the NVIDIA graphics card to work: [https://afterhourscoding.wordpress.com/2014/04/30/dell-l502x-optimus-support-on-ubuntu-14-04/](https://afterhourscoding.wordpress.com/2014/04/30/dell-l502x-optimus-support-on-ubuntu-14-04/).  I have no idea why my computer is freezing up but any help would be greatly appreciated.  
Thanks and God bless,
Caleb Jefferies

---

### Post by Caleb_Jefferies on 2015-06-03
No answers as to why this is happening?  One more thing is that when I open the laptop from suspend mode, all the keyboard commands I made while the laptop was frozen all of a sudden do what they were supposed to do when they were frozen.  Thanks again to anyone who can help. 
God bless,
Caleb Jefferies

---

### Post by egeezer on 2015-06-03
I can't help directly, but you might try searching this forum for Optimus and for Nvidia 331.  I will say I had endless hassles on my desktop with Nvidia 331.

---

### Post by Caleb_Jefferies on 2015-06-04
Actually I got it figured out.  The NVIDIA graphics is not very good and freezes while my integrated graphics card is reliable.  Even though my NVIDIA is very powerful (I believe it is the NVIDIA 525m) it crashes sporadically.  I typed "nvidia-settings" into the terminal and switched the graphics card that is used to my integrated.  Thanks and God bless,
Caleb Jefferies

---

