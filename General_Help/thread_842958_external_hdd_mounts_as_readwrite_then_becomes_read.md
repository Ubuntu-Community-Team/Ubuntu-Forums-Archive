---
title: "external hdd mounts as read/write then becomes read only??"
date: 2008-06-27
forum: General Help
---

### Post by citizenchris099 on 2008-06-27
the subject says it all...i'm running xubuntu 8.04. My external Western Digital External HDD is connected via a pci usb 2.0 card. The drive shows up in Thunar upon booting and is read/write capable. After about 15-20 min or so the drive shows up in Thunar w/a lock icon and though its permissions say its read/write still it is in fact read only. 
Whats going on???

---

### Post by citizenchris099 on 2008-06-27
btw this error does not occur when ex hdd is plugged into the usb 1.0 slots

---

### Post by ianbrown75 on 2008-06-28
just want to say becareful on this subject, I lost 15,000 songs trying to fix this. and now i have a blank hard drive with the same problem.

---

### Post by citizenchris099 on 2008-06-28
^^ I hear ya man. I got over a hundred gb of music plug who knows how much video...i want it safe.

---

### Post by chrisccoulson on 2008-06-28
A drive will go read-only as a precautionary response to a filesystem panic, normally caused by filesystem errors. You need to fix those errors to stop it from happening. What type of filesystem is it?

---

