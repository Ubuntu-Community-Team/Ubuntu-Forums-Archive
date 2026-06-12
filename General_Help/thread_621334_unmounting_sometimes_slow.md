---
title: "unmounting sometimes slow"
date: 2007-11-23
forum: General Help
---

### Post by desklamp on 2007-11-23
Sometimes unmounting is slow.  Why is that?

---

### Post by public_void on 2007-11-23
When copying many files to a device, say a USB stick, the files are not copied straight away. In Linux they are buffered and copied in the background. When you want to unmount a device all the remaining files need copying. Removing the device without unmounting may cause copied files to not appear.

---

