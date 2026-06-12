---
title: "[ubuntu] Boot Manager Problems After Installing Ubuntu"
date: 2016-03-15
forum: General Help
---

### Post by cole11 on 2016-03-15
Ok, so after I installed Ubuntu I went to my boot manager (HP Laptop [F9 key]) the only options I have are, todhiba hard drive with the name ubuntu and boot from efi file. There's no CD ROM option. I want to go back to windows but the problem is, is with the no CD ROM plus there's no USB option. Please help!! Images: [http://imgur.com/a/e4yqi](http://imgur.com/a/e4yqi)

*i am not dual booting, also correction I'm installing a diff distro.

---

### Post by grahammechanical on 2016-03-15
You need to change the UEFI boot order. What you see there is a list of places where the motherboard will look for an OS. If it does not find an OS at the first location in the list it will look for an OS at the second location in the list, and so.

But you now have an OS at the first location. So, the motherboard looks no further than OS boot manager. You need to re-order the list so that one of the other options is at the top and OS boot manager is second.

At the right side of the settings window is a panel that is not included in your image. I am sure that will contain instructions on how to reorder the list.

Regards.

---

### Post by cole11 on 2016-03-16
Ive switched the OS Manager or whatever with The 2nd one I believe and F9 still just shows EFI and HDD ubuntu no Cd Rom

---

