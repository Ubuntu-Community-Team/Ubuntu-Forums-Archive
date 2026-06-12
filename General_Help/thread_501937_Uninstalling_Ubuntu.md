---
title: "Uninstalling Ubuntu"
date: 2007-07-15
forum: General Help
---

### Post by Popolop on 2007-07-15
Can someone help me on how to uninstall Ubuntu. I've had it for a bit, and I decided it's not for me. I already have XP on this computer, if that helps.

---

### Post by mikewhatever on 2007-07-15
Use this [http://www.users.bigpond.net.au/hermanzone/p18.htm](http://www.users.bigpond.net.au/hermanzone/p18.htm)

---

### Post by Popolop on 2007-07-16
> **mikewhatever said:**
> Use this [http://www.users.bigpond.net.au/hermanzone/p18.htm](http://www.users.bigpond.net.au/hermanzone/p18.htm)

Is there a way to do it without the Windows CD? 'Cause I can't find it...
>.>

---

### Post by bdtgp on 2007-07-16
you could just go into Computer Management (when youre in XP) and then click on disk management.  right click on the partition that Ubuntu is on and click Delete Volume.  Then right click on the part that Ubuntu is on and click Extend Volume and then do that so that you know have the XP partition extended to the end.  Youre done.

I gave you the commands that are in Vista, I think it is very similar in XP.  I would try Ubuntu again after Gutsy comes out.

---

### Post by mikewhatever on 2007-07-16
> **bdtgp said:**
> you could just go into Computer Management (when youre in XP) and then click on disk management.  right click on the partition that Ubuntu is on and click Delete Volume.  Then right click on the part that Ubuntu is on and click Extend Volume and then do that so that you know have the XP partition extended to the end.  Youre done.

I gave you the commands that are in Vista, I think it is very similar in XP.  I would try Ubuntu again after Gutsy comes out.

No! Don't do it! First, you have to put the Windows boot loader to the MBR. Use either Super Grub Disk or fixmbr.exe from the link I posted.

---

### Post by louieb on 2007-07-16
> **mikewhatever said:**
> No! Don't do it! First, you have to put the Windows boot loader to the MBR. Use either Super Grub Disk or fixmbr.exe from the link I posted.
Aw come on mikewhatever the guy deserves to have his PC turned into a doorstop for a while.  Seriously mikewhatever is right you have to point your MBR code back to windows before wiping out  Ubuntu. Mike gave you the same link I would have given you.

---

