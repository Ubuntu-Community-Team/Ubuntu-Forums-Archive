---
title: "No Sound under vmware"
date: 2006-12-16
forum: General Help
---

### Post by cacharreo on 2006-12-16
I have just installed vmware with vmware tools, the problem is that the host sound card is not detected, I have been looking for threads about this to fix the problem but I have foiund nothing.
Somebody knows how to?
Thanks!!

---

### Post by jocko on 2006-12-16
You need to add a sound adapter to the virtual machine. This is how to do it:

Power down the virtual machine and click "edit virtual machine settings".
If you don't see a sound adapter in the device list, click "add" and find "sound adapter" in the list.
Click "next".
Instead of "Auto detect", select your actual sound device. (I'm not sure what that will be for you. For me it's /dev/dsp)

Good luck!

---

### Post by drobvice on 2006-12-19
Do you install your windows drivers like you normally would?  I added this and still don't have sound.  Virtual Windows identified it as a soundblaster card.

*Edit* The answer appears to be no.  Hmmm...



*Edit2* All it took was rebooting my computer and restarting the vm and it worked!

---

