---
title: "Bug Report: Copy &amp; Paste"
date: 2008-01-04
forum: General Help
---

### Post by nami on 2008-01-04
If I want to copy and past something from 1 program into another program it works fine.  For example, copying text from a webpage in firefox and pasting it into gedit.  However, if I copy text from 1 program and before pasting it into another program, I close the first program, the copied text seems to get lost so pasting into the second program does not work.  So, for example, if I copy text from a webpage in firefox and then close firefox, if I then try to past it into gedit, it will not work.

Why is that?

---

### Post by LaRoza on 2008-01-04
It is not a bug. 

Linux doesn't have a clipboard.

You can get a clipboard like app for Linux, so it works the way it does in Windows.

---

### Post by jespdj on 2008-01-04
Also, the forums are not the right place to report bugs.
If you find a real bug in Ubuntu, then report it in Launchpad: [https://bugs.launchpad.net/ubuntu](https://bugs.launchpad.net/ubuntu)

---

### Post by LaRoza on 2008-01-04
> **jespdj said:**
> Also, the forums are not the right place to report bugs.
If you find a real bug in Ubuntu, then report it in Launchpad: [https://bugs.launchpad.net/ubuntu](https://bugs.launchpad.net/ubuntu)

True, but it isn't a bug.

---

### Post by TheExplorer on 2008-01-04
The same with Windows.

---

### Post by yopnono on 2008-01-04
> **LaRoza said:**
> It is not a bug. 

Linux doesn't have a clipboard.

You can get a clipboard like app for Linux, so it works the way it does in Windows.

It does have a clipboard, it's just that it don't save the data from IE: firefox if you close it, before you paste it.

It does save it from gnome apps to gnome apps.

However, install glipper for gnome or klipper for kde.You will find it the the synaptic.

---

### Post by jespdj on 2008-01-04
> **LaRoza said:**
> True, but it isn't a bug.
That's why I said **"If you find a real bug..."** :rolleyes:

---

### Post by nami on 2008-01-04
Thanks.

Looking into glipper.

---

### Post by mikewhatever on 2008-01-04
> **nami said:**
> If I want to copy and past something from 1 program into another program it works fine.  For example, copying text from a webpage in firefox and pasting it into gedit.  However, if I copy text from 1 program and before pasting it into another program, I close the first program, the copied text seems to get lost so pasting into the second program does not work.  So, for example, if I copy text from a webpage in firefox and then close firefox, if I then try to past it into gedit, it will not work.

Why is that?

It may not be a bug, but seems to be a good idea for the next release to take care of. Someone told me that KDE does have a clipboard, but Gnome does not. I do not know about XFCE. Anyway, nami, I've added the functionality you wanted by installing glipper package from the repositories. It can hold a number of entries of defined length, but must be running to be usable. I've tested it with Firefox and Gedit before posting.

---

