---
title: "Removing LUKS"
date: 2008-02-22
forum: General Help
---

### Post by Saxu on 2008-02-22
Hello,

I installed ubuntu with luks some time ago and I would like to use the drive now with windows. Is there a way to completely remove the luks encryption from the harddrive?

Sincerely,

Saxu

---

### Post by banewman on 2008-02-22
A format should remove it.

---

### Post by Saxu on 2008-02-22
> **banewman said:**
> A format should remove it.

Hey,

Tried to format the drive with my WinXP cd and im getting Genreral Protection Fault (00000000D)

Any ideas?

Sincerely,

Saxu

---

### Post by st1 on 2008-04-15
A General Processing Fault from a windows distribution can be many things, not necessarily a hardware error. Ref: [http://en.wikipedia.org/wiki/General_protection_fault](http://en.wikipedia.org/wiki/General_protection_fault)

You could try to format the hd through parted (you would probably want to use gparted) or through an installation cd from *ubuntu. If you get the same gpf code through this method, you have yourself a very nice shelfstopper.

---

