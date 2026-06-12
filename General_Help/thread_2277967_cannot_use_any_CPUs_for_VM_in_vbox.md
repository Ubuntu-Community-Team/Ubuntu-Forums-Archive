---
title: "cannot use any CPUs for VM in vbox"
date: 2015-05-12
forum: General Help
---

### Post by kevin164 on 2015-05-12
my vmachine is getting this error (VERR_SVM_DISABLED). I assume it has something to do with the fact that I can't allocate any CPU cores on my VM. Can anyone help?
[COLOR=#000000]edit: I just noticed that there is no option for a 64-bit OS. I have a 64-bit processor, perhaps I need some drivers? AMD FX series 6-core[/COLOR]

---

### Post by QIII on 2015-05-12
Hello!

Have you checked your BIOS/UEFI settings to make sure AMD-V is enabled?

---

### Post by kevin164 on 2015-05-12
yes, they're enabled right now. But again, it seems like my OS (mac) is 64-bit. This seems to be the problem considering there is no option for a 64-bit system on ANY OS

---

### Post by kevin164 on 2015-05-12
turns out, when I say left, mu mobo goes right. AMD virtuilization was NOT enabled. It is now. Fixed the problem, thank you

---

### Post by QIII on 2015-05-12
Sometimes it takes me three days of frustration to see something like that.

Glad you got it working.

Please mark your thread "Solved" to help others find the solution.

---

