---
title: "Video Driver Trouble"
date: 2007-10-27
forum: General Help
---

### Post by wildcat1980 on 2007-10-27
I just installed Gutsy fine-tuning it the way I liked it.  I installed the drivers from my faster nvidia graphics card.  With the resolution too small, I adjusted the settings where I was prompted to reboot.  
Before I was asked to login, an error screen told me I had to specify a screen resolution before I could continue.
I did.
When I rebooted, the whole screen is a mess, unable to see anything on it.  
If I can't see, how do I readjust the resolution or go back to  original open source drivers?  My video card worked fine with feisty.
Any ideas short of just reinstalling feisty from scratch?
I do have windows in another partition till this is resolved, which I will one way or the other!
Thanks guys!

---

### Post by pieisgood4589 on 2007-10-27
When booting, hit escape when it says to, and key in "you are so gullible I have no idea what I'm doing -s" and hit enter. Then, reinstall the system, and install the drivers, and choose the resolution that you use in Windows. It will work. Trust me.

---

### Post by wildcat1980 on 2007-10-27
My apologies for making such an elementary, stupid a** mistake as the one I just did!  I was unaware that changing the resolution settings that ubuntu offered to a better one, rebooting, having trouble was a sin in the ubuntu bible!  
If this is the best advice given to beginners, it's clear why there are so many windows users!  Good day sir.

From: Someone who works 10-12 hours a day 5-6 days a week and just wants things to work sometimes without dealing with grief...

---

### Post by Maestro23 on 2007-10-27
> **wildcat1980 said:**
> I just installed Gutsy fine-tuning it the way I liked it.  I installed the drivers from my faster nvidia graphics card.  With the resolution too small, I adjusted the settings where I was prompted to reboot.  
Before I was asked to login, an error screen told me I had to specify a screen resolution before I could continue.
I did.
When I rebooted, the whole screen is a mess, unable to see anything on it.  
If I can't see, how do I readjust the resolution or go back to  original open source drivers?  My video card worked fine with feisty.
Any ideas short of just reinstalling feisty from scratch?
I do have windows in another partition till this is resolved, which I will one way or the other!
Thanks guys!

Can you boot into Recovery Mode? If so...

At the command line, enter the following command:

> sudo dpkg-reconfigure xserver-xorg

Accept the deaults and make sure to pick your desired resolution.  This will allow you to get to the desktop.  You can go from there to get your correct driver.

---

### Post by markharding557 on 2007-10-27
> **pieisgood4589 said:**
> When booting, hit escape when it says to, and key in "you are so gullible I have no idea what I'm doing -s" and hit enter. Then, reinstall the system, and install the drivers, and choose the resolution that you use in Windows. It will work. Trust me.

you are an idiot and a disgrace to ubuntu and its forums frankly  your bad attitude stinks,most of us on this forum take pride in helping others where we can you obviosly do not if i were a mod you would be banned imediatly 
as for the unfortunate person concerned reinstalling is probably your simplest option

---

