---
title: "Woah, what happened?"
date: 2006-11-05
forum: General Help
---

### Post by m.musashi on 2006-11-05
I just installed an update. It seened to be a new version of the kernel. When I rebooted I had an x server failure. It seems my nvidia driver was uninstalled or something. I had to go back to the "nv" driver to get the gui to load. I was running beryl and had the beta nvidia driver and the 386 kernel. I'm not sure what happened but I can no longer run beryl and my nvidia splash is gone (so I assume no nvidia driver).

Anyone else see this?

Sorry. I'm on edgy.

---

### Post by CatKiller on 2006-11-05
You should always check to see what's going to be uninstalled when you install something new, in case it was something you wanted. As you've just found out.

I think it's the restricted modules that you need for the nVidia driver to work, isn't it? You could try reinstalling them, and the nVidia drivers, and wait for either a newer restricted modules package that will work with your driver, or a newer driver that will work with the newer kernel.

Good luck.

---

### Post by taurus on 2006-11-05
Yes, each time you upgrade a kernel, you need to reinstall nvidia driver again...  But if you use "nv", then you don't have to do anything!

---

### Post by m.musashi on 2006-11-05
I did check and it said something about nvidia xgl. Since I had installed the aiglx driver I assumed that was not the same. Guess again... Oh, well, live and learn. I'm off to try and reinstall it all. Thanks for the input.

---

