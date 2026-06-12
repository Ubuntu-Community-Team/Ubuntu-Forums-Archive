---
title: "Library conflict - broken package problem - help???"
date: 2007-01-09
forum: General Help
---

### Post by paulhollow on 2007-01-09
Hi - a have a problem with a broken package (reported by Synaptic package manager) due to two applications trying to use different versions of the same package - can anyone help?

I have installed both DVDStyler and Cinelerra on my Edgy system, and it is these two which are conflicting...

I use DVDStyler to produce/author DVDs - but this has libmjpegtools0c2a as a dependancy. I removed both libmjpegtools0c2a and DVDStyler in order to install Cinelerra (which uses libmjpegtools0 1:1.8.0-0.4), which worked ok.

I then reinstalled DVDStyler (from Synaptic package manager) but this complained that it could not install libmjpegtools0c2a as it conflicted with libmjpegtools0.

However, both Cinelerra and DVDStyler are now working fine together (both, i guess, using libmjpegtools0, not 0c2a...) but Synaptic package manager is now complaining that it has a broken package and wants to remove libmjpegtools0c2a - but if i let it, it will also remove DVDStyler...which i want to keep...

Is there any way i can make both packages co-exist? Or can i persuade DVDStyler to use libmjpegtools0 instead of ...0c2a? Or can i get Synaptic to ignore this one broken package (as at the moment it won't let me install updates)?

Any help appreciated!!!! Thanks in advance!

Paul

---

### Post by kwacka on 2007-01-13
deleted

---

