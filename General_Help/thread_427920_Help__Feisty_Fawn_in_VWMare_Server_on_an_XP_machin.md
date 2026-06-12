---
title: "Help:  Feisty Fawn in VWMare Server on an XP machine very laggy."
date: 2007-04-29
forum: General Help
---

### Post by pooter on 2007-04-29
I had a free Sunday, so I decided to get my feet wet with Linux via Ubuntu.  My host machine is running XP Pro on an E6400 Core Duo with 2 gigs of RAM and an NVidia 7900 GT.  I dedicated 1 gig for my FF install.  

Everything installed fine and I have VMWare Tools running, however there is a very noticable lag.  If I drag a window from one side of the screen to the other, there's about a .5 second lag.  Similarly, scrolling up and down windows is very unresponsive.   I read that on a dual-core, the experience should be very similar to running it natively.  Is there anything I can do to speed things up?

Also, not quite as important but can I get my mousewheel working too?  It's a Logtiech mouse.

Please let me know if you need any more information.  Thanks!

---

### Post by Ziox on 2007-04-29
Do you have the native VM support enabled on your processor?

When your machine boots, go into BIOS and check to see if it is set.

also, since you are using a VM, then I suspect that Ubuntu is using the standard Vesa graphics driver, which even creates lag on my decent laptop natively.  But since VM uses a generic graphics card, I guess the driver must be Vesa

As for you mouse problem, in FF, open up a terminal and enter the command "xev"
A small window should pop up.  Place your cursor inside that box and scroll.  In the terminal window you should notice text scrolling by.  You should to find what "button" each scroll is registered as.  Usually the scrolls are registered as button 4 and 5.  However, if they are not registered correctly, then the problem might be on VM's part.  If VM doesn't relay the signal from the mouse to FF correctly, then I don't think there is a way to enable mousewheel within FF.

---

### Post by pooter on 2007-04-29
> **Ziox said:**
> Do you have the native VM support enabled on your processor?

When your machine boots, go into BIOS and check to see if it is set.

also, since you are using a VM, then I suspect that Ubuntu is using the standard Vesa graphics driver, which even creates lag on my decent laptop natively.  But since VM uses a generic graphics card, I guess the driver must be Vesa

As for you mouse problem, in FF, open up a terminal and enter the command "xev"
A small window should pop up.  Place your cursor inside that box and scroll.  In the terminal window you should notice text scrolling by.  You should to find what "button" each scroll is registered as.  Usually the scrolls are registered as button 4 and 5.  However, if they are not registered correctly, then the problem might be on VM's part.  If VM doesn't relay the signal from the mouse to FF correctly, then I don't think there is a way to enable mousewheel within FF.

Thanks for your help.  I had VT enabled, but the bios was a few versions behind, so I updated that and got the latest infs.  It seemed to help a bit, but may just be placebo.  The experience is now akin to using VNC across a fairly decent Internet connection.  In any case, it's good enough to let me screw around without too much frustration.

---

### Post by veloce on 2007-05-01
And finally, switch around your host and virtual operating systems! :) 

VMware runs hugely better under Ubuntu than XP.  I get better performance from my XP vms than I got natively.  Ubuntu just manages memory better.

---

