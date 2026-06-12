---
title: "simh - what's the proper place to store disk images?"
date: 2021-12-09
forum: General Help
---

### Post by uacnt83982803 on 2021-12-09
I've installed simh (so I can run various DEC operating systems).  

I have also downloaded and extracted the various disk image files (.dsk) that I need for the simulator.

What is the correct (meaning, following Linux conventions) folder location to store these disk images, and any other data files as needed?  This isn't clear, at least in the simh installation documentation that I've read through.

Thanks for any help.

---

### Post by TheFu on 2021-12-12
Any data location with sufficient space?
I'd mount a separate logical volume to hold them, probably under /Data/.  Just not in a HOME director or in any place else that already exists.
Do they haven't an Alpha 140 simulator? I could be entertained for 30 minutes running OSF/1 again.  QEMU probably has this covered.

Ah, I see this is for much older hardware.

---

