---
title: "Remastersys Boots Into DELL Recovery"
date: 2013-03-11
forum: General Help
---

### Post by Mike Green9 on 2013-03-11
Ubuntu 12.10    Remastersys v 3.0.4-2   on an old DELL Desktop using BIOS                   Mar.11.2013


Hi.

I created an ISO image using Remasterys, and burned the image to a DVD.

The remastersys live DVD boots (3.6gb), and gives me the usual options of installing the LIVE CD/DVD, or Restoring the System. Regardless of which option I choose, I end up at a DELL Recovery Screen, which gives me 2 further options:
         'Restore Entire System'     or  
         'Restore Only Linux OS'
         
I have no idea why this screen is coming up, but it has the Ubuntu Icons and top Menu Bar in a window that takes up 1/4 of the screen, with Ubuntu original brown colours.

If I choose 'Restore Only Linux OS' and 'Continue', I'm in an infinite loop. However, if I click on 'Quit' anytime in the loop, up comes my beloved Desktop. All looks AOK at that point.

When I click on either of the Install Icons, I'm back to yet another DELL Recovery Screen, which says: "Error: This recovery media only functions on a Dell System."

A FEB.12.2013 Remastersys Live DVD works fine. Other than regular Ubuntu System Updates, nothing has changed.

I don't know if this has anything to do with Ubuntu Patches and Secure Boot issues?? Can anyone help?


Thanks,

M...

---

### Post by Dreamer Fithp Apprentice on 2013-03-12
I had a similar issue once, and for what it is worth (probably not much if "using BIOS                   Mar.11.2013" means you updated your bios yesterday) I got rid of it by downloading a bios update program from IBM which I burned to a CD and booted to update my bios. Darned if I know why that worked but it did. Might be worth a try even if your bios is up to date. Maybe firmware can get corrupted? If not we should consider replacing congressmen with chips. They certainly couldn't be any dumber.

---

### Post by Mike Green9 on 2013-03-12
> **Dreamer Fithp Apprentice said:**
> I had a similar issue once, and for what it is worth (probably not much if "using BIOS                   Mar.11.2013" means you updated your bios yesterday) I got rid of it by downloading a bios update program from IBM which I burned to a CD and booted to update my bios. Darned if I know why that worked but it did. Might be worth a try even if your bios is up to date. Maybe firmware can get corrupted? If not we should consider replacing congressmen with chips. They certainly couldn't be any dumber.


Hi.

...replacing congressmen with chips... now that's  funny. And cheaper too.

My DELL is at least 10 years old, and I haven't upgraded the BIOS since 2006. 

Now here is what baffles me - When I boot the Feb. 2  Remastersys DVD (I just tried it again), it works fine. When I boot the March 1 Remastersys DVD, I end up in the DELL recovery screen. It appears that Ubuntu updates have caused the problem. I would think others would have the same problem.

I don't know how many are actually using Remastersys - it is a great product.


M....

---

### Post by Mike Green9 on 2013-03-30
Hi.

I found my problem. I had a package called "DELL-Recovery" installed on my Ubuntu 12.10 system. Using Synaptic Package Manager, I uninstalled it, and the problem is now history.

I am having other issues with ubiquity, but that is another topic.

More insight into the problem can be found here:

[http://www.remastersys.com/forums/index.php?PHPSESSID=d1loiq3regui5907919888nhj2&topic=2190.0](http://www.remastersys.com/forums/index.php?PHPSESSID=d1loiq3regui5907919888nhj2&topic=2190.0)


Thanks,

M...

---

