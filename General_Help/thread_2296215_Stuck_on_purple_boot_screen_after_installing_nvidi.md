---
title: "Stuck on purple boot screen after installing nvidia drivers"
date: 2015-09-24
forum: General Help
---

### Post by domino4 on 2015-09-24
So after installing Ubuntu 15.04 on my pc in dual-boot with Win10, and installing the proprietary nvidia drivers for my graphics card, I am now stuck on the purple boot screen, even if I use the "nomodeset" option in grub, what gives, I can't even get into the OS now? There must be something I am missing, it's the second time I try to install ubuntu today, and I am always left with the same problem. I hope you guys can help me, thanks.

Z97-G5/i5-4690k/GTX 980ti

---

### Post by Bucky Ball on 2015-09-24
Welcome. Which Nvidia driver are you trying to install for the GTX 980ti, where are you installing it from and how?

If you installed and Ubuntu was running fine without them, for what reason are you needing the proprietary driver? Have you got a problem with graphics with the open-source Noveau driver?

How are you applying the nomodeset option? You should test with a boot first so remove it from grub if you have added it to any files. That could confuse things further.

You can do this by hitting control+alt+F1 at the purple screen (hopefully), login, change the file back to their original state.

---

### Post by domino4 on 2015-09-24
Thanks for your reply. I was installing the Linux x64 (AMD64/EM64T) Display Driver 352.41 (.run file), from the menu Shift+Alt+F1 (not so sure how it's called).
Also I could not change my display resolution, and I wanted the optimal performance possible, so I fugured it would be best to opt for the official drivers.
No, I haven't had time to add it to any file, I simply boot up and edited the booting options, but even booting without editing it does nothing.

---

