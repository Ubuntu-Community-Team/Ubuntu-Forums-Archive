---
title: "About to give up on Ubuntu LiveCD.  Help please."
date: 2005-08-23
forum: General Help
---

### Post by knandyal on 2005-08-23
All,

I am trying to boot Hoary on my new HP Pavilion Dv4040us (Centrino chipset, 1GB RAM, 15.4 inch wide screen LCD).

The livecd boots up and goes through the motion of keyboard/language/driver selection etc.  However as it initialises into graphic mode, it just shows translucent screen (but I can tell that it boots properly into fraphic mode, because I hear the welcome tune, and I can also see the text console when I press ctrl+1 and I can ping it too, from another server).  The screen just wont display anything.  

I have tried various screen resolutions, but none help.

Eventhough I love to use ubuntu, If this doesnt work, I am out of choices but to use Linspire, which seems to work the screen nicely.

Thanks
Karthik

---

### Post by glug101 on 2005-08-23
My guesse is an xsettings issue.  Might need to run X --setup from the text screen to get the screen to work.  When I recently installed Ubuntu on my brothers computer with an intel graphics chipset, Ubuntu did not detect the card correctly and was stuck at 640x480.  There might also be a problem with the resolution settings of your wide screen.  Again, X --setup should allow you to adjust for this.  

Laptops are notoriously finnicky in linux though, and you might just be better off with Linspire if it automatically detects your hardware. (However, I understand the preference for Ubuntu, it's really slick!)  Maybe Breezy Badger will have better support?

---

