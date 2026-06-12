---
title: "run wubi from &quot;bootable&quot; CD?"
date: 2007-05-17
forum: General Help
---

### Post by raybaron on 2007-05-17
Is it possible to create a bootable CD and install Wubi to that driver and not go through the boot.ini mechanism. I'm a newbie here and trying to isolate Ubuntu from Windows and eventually dump Windows altogether.
thx,
Ray

---

### Post by tuxcantfly on 2007-05-17
if what you're trying to do is isolate ubuntu from windows, wouldn't transferring it to its own partition do the job? I don't understand why you'd need to put it on a bootable cd... Anyhow, this utility can do the job for you (note that I'm still in the process of testing it, wouldn't exactly recommend using it just yet) I'll post an update and a nice guide once it's ready for the masses: [https://launchpad.net/lvpm](https://launchpad.net/lvpm)

Alos, note that the wubi disk images reside on the windows partition, so unless you move them to a dedicated partition, you still won't be able to remove windows and keep ubuntu, moving the bootlaoder to a cd is not enough

---

### Post by fitnessforyoutoo on 2008-10-10
> **raybaron said:**
> Is it possible to create a bootable CD and install Wubi to that driver and not go through the boot.ini mechanism. I'm a newbie here and trying to isolate Ubuntu from Windows and eventually dump Windows altogether.
thx,
Ray

I have a bootable CD I got from my wife's cousin, it is great for traveling abroad because it leaves no trace you have been on someone else's machine.

If you use a public computer no one can get information or passwords you used or see where you have been.

I was just looking on here to see if anyone else had it, he said he made the code to make mine work.

---

