---
title: "eMachine won't power down"
date: 2007-08-12
forum: General Help
---

### Post by wadebear on 2007-08-12
Computer: eMachine T3522 (stock)

OS: Feisty Faun 7.04

Problem:  When I try to shut down the machine it hangs on the splash page and never powers down.  I have to hold the power button for several seconds for the machine to power down.

This may be an APCI issue with the system BIOS.  My options there are S1 and S3, I have tried them both.

As a starting point for diagnosing the problem, could someone tell me how to turn off the graphic image so I can see what is happening as the machine shuts down.  At least that way I can find out if the machine is just not powering down, or if it is hanging on some process before it reaches that stage.

---

### Post by uclalinux on 2007-08-12
i had the same problem, most likely it is some thing in your mother board bios, or you have the jumpers set up wrong when you connected them to the motherboard.

---

### Post by louieb on 2007-08-12
To remove the splash on startup / shutdown edit /boot/grub/menu.lst find the kernel and remove **quiet splash** from the line. 
 
OR when the machine boots highlight the Ubuntu entry and press **e** this will allow a one time edit of the entry (that is any change made will not be saved but just used for one boot). and make the same edit. Press enter then press **b** to boot

---

### Post by wadebear on 2007-08-13
Thank you, that worked.

The operating system seems to be shutting down, the signal to power down the machine just does not seem to be getting through.

At least I can go ahead and get this machine set up.  It's for the customers at our campground to use.

---

