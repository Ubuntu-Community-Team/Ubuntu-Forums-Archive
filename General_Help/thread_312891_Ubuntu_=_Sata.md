---
title: "Ubuntu = Sata"
date: 2006-12-05
forum: General Help
---

### Post by ESPOiG on 2006-12-05
im building a new computer and my plan is to have 3x hdds, 1 for win/games 1 for ubuntu and 1 for file share, ive never used a sata hdd for an os and wanna know if the things i hear are true

1st of all is that when you goto install windows xp on a sata hdd rather than an ide it requires drivers to be installed via floppy disk for windows installer to be able to detect and see the hdd??

next if this is so, does the linux kernel detect sata hdds for an installation so when i goto install ubunut to one of my sata hdds will it work, will i have problems etc??

and if not and linux is ok whats the workaround if you dont want to bother with a floppy

anyway thankyou in advance for any ideas/comments of this topic

---

### Post by igknighted on 2006-12-05
Linux should in almost all cases have no trouble with SATA... if you have a very new motherboard the controller *may* not be recognized, and the same goes with very old systems with an SATA card added, these may also have issues.  Otherwise, linux and SATA is smooth sailing.

As for windows, well, I don't use windows at all, but I did try to help a friend reinstall windows onto his SATA disk and it was a nightmare of google searching and some forum searching to finally figure it out.  This was all several months ago so I really can't even begin to describe what we did.  If I remember correctly it wasn't difficult, just obscure.

---

### Post by ESPOiG on 2006-12-05
thanks that sorta helps :D... anyone else know anything about this windows + sata problem??

---

### Post by princemackenzie on 2006-12-05
> **ESPOiG said:**
> i
1st of all is that when you goto install windows xp on a sata hdd rather than an ide it requires drivers to be installed via floppy disk for windows installer to be able to detect and see the hdd??

It depends.  Some motherboards can emulate SATA drives as older PATA drives and windows will see them without drivers.  Other mobos require a floppy disk with the driver on there provided during installation.  Its a pain.  I have an nForce mobo which did not need a floppy disk an a radeon Xpress mobo which did, and both run off of SATA HDs.

> next if this is so, does the linux kernel detect sata hdds for an installation so when i goto install ubunut to one of my sata hdds will it 
work, will i have problems etc??

On both these machines, Ubuntu saw my SATA drives automagically.  (No extra anything needed).

> 
and if not and linux is ok whats the workaround if you dont want to bother with a floppy

You shouldn't need any "extra" drivers or workarounds.

Please post if you need more info, and I'm glad I could help.

---

