---
title: "[SOLVED] After Update I boot to blank screen???"
date: 2008-05-29
forum: General Help
---

### Post by radamo on 2008-05-29
Last weekend I updated my Ubuntu 8.04 Hardy install to the latest kernel .17 (I think).  Since the update if I boot into the new kernel and login when X starts I have a blank screen.  The system appears to be running since I clicked the mouse around and was able to Log Out (sheer luck).  

If I boot back to .16 all is fine... Does anyone have any idea how I can deal with this?
Thanks,
RA

---

### Post by fyo on 2008-05-29
You wouldn't be using NVIDIA (or possiby ATI) downloaded drivers for your graphics card, would you?

The kernel update necessitates recompiling / reinstalling the NVIDIA drivers if you downloaded via nvida.com (i.e. if you got the latest drivers at some point). In that case, you need to run the driver package again (which, in my case with a 64bit Ubuntu 8.04 system, meant that it recompiled the interface).

---

### Post by radamo on 2008-05-29
Actually I do have an ATI card and am using Envy to keep it current.  Envy shows version 8.3 at last look. Which appears to now be 2 versions back...

Is that my issue?  If so I will try the recovery mode to see if I can install from there...

Thanks,

RA

---

### Post by fyo on 2008-05-29
> **radamo said:**
> Is that my issue?  If so I will try the recovery mode to see if I can install from there...

I know the NVIDIA drivers like to behave like that after a kernel update, so it's certainly a likely candidate.

What happens if you switch to a console (e.g. ctrl-alt-2)? That's not X, so it shouldn't care about your drivers (default console for X is 7).

---

### Post by radamo on 2008-06-02
Used recovery mode and "Rebuilt X Server"... Worked like a charm.
RA

---

