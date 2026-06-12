---
title: "White blinking line...nothing else."
date: 2012-12-03
forum: General Help
---

### Post by Nevakonaza on 2012-12-03
Hey guys,
 
I have the following old system that i want to set up as a web browsing machine.
 
AMD Sempron 2800+ 2Ghz,A7V8X-LA motherboard,1.25Gb PC3200 Ram,120Gb IDE hard drive,ATI 9600 Pro 256mb graphics card.
 
Now i seem to be having the same issue with Ubuntu and i also tried Linux Mint.
 
Both installed fine,but when i boot the fresh install for the first time  from the hard drive all i get is a black screen with a blinking white  line at the top and nothing more...does not boot to desktop.
 
I taken out the 9600 pro graphics card as i thought maybe that was causing an issue...still the same.
 
 
totally lost,Appreciate any help guys.
 
thanks!

---

### Post by jim_deadlock on 2012-12-03
This is quite common with a new install. What you need to do is on the initial grub screen, press e to edit the boot options, then add nomodeset to the end of the line that starts with linux (or in some cases you have a dropdown menu where you can select nomodeset).

You should only need to do this once because the first time you run your updates you will get a graphics driver and next boot should be OK.

---

### Post by Nevakonaza on 2012-12-04
Thanks for your reply,Ive just installed ubuntu-12.04 LTS instead of the latest,and now it boots to desktop just fine without the need of adding "nomodeset" so everything's good now. :-D

Thanks again.

---

