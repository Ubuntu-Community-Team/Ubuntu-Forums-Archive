---
title: "Firefox Segmentation Fault in VNC"
date: 2007-08-07
forum: General Help
---

### Post by htpeng on 2007-08-07
I just installed Ubuntu a couple of days ago.  It came w/ Firefox 2.0.0.6.  It works locally.  But when I try to start Firefox from VNC (other apps works fine in VNC), it always came back w/ Segmentation Fault.

Any pointers? Thanks

---

### Post by joel.sherrill on 2007-08-07
Not that this helps either of us a lot but I have a very similar problem on Fedora 7.  It did NOT happen on Fedora Core 6 on the same hardware and immediately started upon upgrade.  

Firefox does not crash for me every time but some pages reliably make it die.  I suspect that the VNC client does not have some feature that Firefox expects all displays to have.

I am using UltraVNC 1.0.1 on Windows. I know it is quite old.  I have no solution but I know this is a reason breakage.  Together we now know it is not specific to Ubuntu or Fedora but to something they share.  Doesn't make you feel better, does it? :confused:

---

