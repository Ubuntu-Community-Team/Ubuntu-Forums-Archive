---
title: "In low graphics mode after  changing sysctl.conf"
date: 2008-06-20
forum: General Help
---

### Post by Pirate King on 2008-06-20
Hi there!

I wasn't really sure where to chuck this thread. It doesn't really seem like exclusively multimedia problem or exclusively a hardware problem, so I figured general would be the go.

Anyway.

**Problem:** After following [http://wiki.winehq.org/PreloaderPageZeroProblem](http://wiki.winehq.org/PreloaderPageZeroProblem) Ubuntu is now running in low graphics mode, and it doesn't detect my graphics drivers. (all else is detected)
**Possible Causes:** I might have accidently changed something in sysctl.conf that I shouldn't have changed. 
**Graphics Card:** Nvidia Geforce 7600GT
**Ubuntu Version:** Hardy Heron x64
**Additional Information:** - It occurred immediately after restarting after editing sysctl.conf. 
- I didn't make a backup of sysctl.conf.

Thanks in advance, any help is appreciated! =)

---

### Post by ashcraft00 on 2008-06-20
This is essentialy the same problem I'm having. I couldn't pin point the exact cause though, I was just updating and then it restarted and installed updates, and this happened.

---

### Post by Pirate King on 2008-06-21
I changed back to vm.mmap_min_addr = 65536 in Sysctl.conf and it hasn't made any improvements.

---

### Post by dedlycow on 2008-06-21
hi there
 I am having same experience. I updated through the update managera fday or so agoand I cannot get any high res than 800 X 600 . I have tried many things with the help of others and am no better off.
 I am using Hardy
nVidia 7600 GS card
It was working fine with Hardy for several weeks since i upgraded to Hardy.

Nvidia server settings appear in System admin. It tells me to  runconfig x i have done this and restarted still does not work.
please help.
dedlycow

---

### Post by Pirate King on 2008-06-22
Perhaps the problem is not related to the [http://wiki.winehq.org/PreloaderPageZeroProblem](http://wiki.winehq.org/PreloaderPageZeroProblem) how-to I followed, but instead the updates.

---

### Post by Pirate King on 2008-06-22
I just updated again, restarted and everything is back to normal.

I suggest you guys try the same thing. 

Yippee, skip!

---

