---
title: "Change golor depth for live CD on Dell lappy?"
date: 2005-08-15
forum: General Help
---

### Post by Spinoza_scholar on 2005-08-15
Problem resolved (sort of).  In case anyone cares, here's what i did:

1. Instead of trying to resolve the Live CD problem, I re-partitioned my HD and installed Ubuntu alongside XP.  
2. I then edited xorg.conf and added the following lines under "monitor":
           HorizSync 31.5 - 48.5
           VertRefresh 59.0 - 75.0

Thanks to Duglass, kelving, sureluvmyspam, and the others in the Hardware support forum.

------------------------------------------------
Hi-

First, thanks to this great community and developers for making this distro - I love it on my desktop.  

But now I'm trying to run Ubuntu or Kubuntu Live CD on a Dell Inspiron 1100 with an integrated Intel 845GL graphics chipset.  I am having a problem:

When I launch from the live CD, my displayed screen is a small box surrounded by several inches of unsuable black screen.  I think this is because the Dell BIOS allocates only 1 MB video memory and this cannot be changed (I've tried and Dell has confirmed this with me).  

I was told that if I set the color depth to a lower setting, then Linux would be able to fill the whole screen with my display.  So...

1. How can I change the color depth during boot-up with a Live CD?
2. Is there some way to hack the Dell BIOS?
3. Is there some other way I can use Ubuntu or Kubuntu on my lappy, so that I do not have this display problem?  

Thanks so much in advance.  


PS:  During the boot-up, I am prompted to choose which resolutions my screen will use.  No matter what I choose, I have the same problem.  The problem starts right from the beginning of the boot-up.  My boot up screen is also smaller than it should be.  Also, I have the newest Dell BIOS (A32).  I also tried changing the resolution once I was inside GNOME, but it doesn't seem to work either.

---

