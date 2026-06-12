---
title: "konqueror broken after upgrade"
date: 2007-04-21
forum: General Help
---

### Post by styracosaurus on 2007-04-21
I just upgraded to Feisty, and am really frustrated. Konqueror, which I use a lot as a file manager and never as a web browser, seems to have been stripped down to the point where I can't fix it. The bar at the top that used to have things like "back," "up", the address bar, etc has been replaced with "zoom" which changes the size of icons, and some sort of filter.

I hope this is not a design choice! It,s awful, I thought "Dolphin" was supposed to serve as a light file manager and Konqueror was staying nice and bloated?

---

### Post by RagingOcelot on 2007-04-21
I just deleted my /home/username/.kde/share/apps/konqueror/ folder and the main toolbar rose from the dead.  Still, annoying...

---

### Post by styracosaurus on 2007-04-21
Thanks a lot!! That worked wonderfully, it makes sense and I'm glad that's all it was.

---

### Post by mocha on 2007-05-08
I had the same problem after upgrading to Feisty and had to copy "konq-kubuntu.rc" to /root/share/apps/konqueror".  Now I can open Konqueror in root mode and have it look like it does in normal user mode.

---

