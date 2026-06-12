---
title: "Login loop and can only get into terminal from Guest."
date: 2013-11-21
forum: General Help
---

### Post by tony-landau on 2013-11-21
Hi folks....Don't know how this happened but I (admin')am stuck in a login loop and can only bring up terminal from guest login with cont/alt T. This doesn't allow sudo so I have been unable to try to remedy the problem. Question....Is there a way to login as administrator from guest terminal. Would love to avoid reinstall so any help greatly appreciated. I'm pretty much an Ubuntu beginner so simplifies answers please.

---

### Post by Impavidus on 2013-11-21
Can you loging using the console? Type ctrl-alt-F1 to get one, ctrl-alt-F7 to get back to the gui. Then check (and possibly repair) the owner and permissions of .ICEauthority and .Xauthority. They are sometimes wrong because of some messing around and may prevent you from logging in to the GUI. Both should be owned by you and have permissions 600 (read and write for owner only).

If you can't get in using the console, you may need the recovery console. You can access it via grub.

---

