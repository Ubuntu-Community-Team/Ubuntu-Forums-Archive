---
title: "USB stick mounting when two users are logged-in at the same time"
date: 2008-06-09
forum: General Help
---

### Post by grof on 2008-06-09
When I plugin my USB stick then it normally mounted in the current user, but if two users are logged-in at the same time and after pluging stick into the USB port, I switch to another user (with fast user switch applet), on the screen of this second user apperaing message that I do not have permissions to mount that stick.

Why this happened, and why not if I insert CD into drive?
Is that some bug in Hardy or what elese?

thx.

---

### Post by fsmithred on 2008-06-10
I've never tried that, but maybe you need to add the second user to the plugdev group. For mounting a cd, you need to be a member of the cdrom group.

---

