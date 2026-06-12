---
title: "Broken UI/ ATI Proprietary Drivers Beta Issues"
date: 2013-08-01
forum: General Help
---

### Post by Hungry Man on 2013-08-01
I installed the latest Beta drivers from ATI, as they supported the 3.10 kernel I was using. It failed to install on the kernel, and I rebooted, and the UI is broken. I can load up a terminal and launch Chrome, or update manager.

I booted into my 3.8 kernel and tried installing. This time it installed "successfully", but the same issue exists - no UI.

Is there a safe way to return to the OSS drivers?

---

### Post by Gnawnsense on 2013-08-01
> **Hungry Man said:**
> I installed the latest Beta drivers from ATI, as they supported the 3.10 kernel I was using. It failed to install on the kernel, and I rebooted, and the UI is broken. I can load up a terminal and launch Chrome, or update manager.

I booted into my 3.8 kernel and tried installing. This time it installed "successfully", but the same issue exists - no UI.

Is there a safe way to return to the OSS drivers?

I just fresh installed 13.04 a bit ago and had been using the AMD 13.6 drivers previous to this fresh install, which were working perfectly for my 6800. I noticed the 13.8 drivers were released just recently so I downloaded them. After installing I rebooted and am hanging on the purple UBUNTU splash page.

Failsafe mode won't work, and all I can really do is get into a terminal. Reinstalling 13.04 again now to avoid the headache and going back to 13.6 for the time being.

---

### Post by Hungry Man on 2013-08-01
I went to the stable closed source drivers, and I have the same issues.

At this point I'd just like to safely return to the OSS drivers, but I don't even know how.

---

### Post by QIII on 2013-08-01
Did you install using the driver from the AMD/ATI website?

If so, do the following in the terminal
```
sudo amdconfig --uninstall
```

---

### Post by Hungry Man on 2013-08-01
I ran that and it said it restored the environment and that it successfully uninstalled. But Compiz still won't load/ the UI is broken in the same way. Is there a way to reinstall the OSS drivers? Update-Manager says I'm using them.

---

### Post by QIII on 2013-08-01
Do you see a file /etc/X11/xorg.conf?

Edit:  actually first -- did you reboot?

---

### Post by Hungry Man on 2013-08-01
Yes, I rebooted.

xorg.conf.failsafe
xorg.conf.fglrx-0
xorg.conf.fglrx-1
xorg.conf.fglrx-2
xorg.conf.fglrx-3
xorg.conf.original-0
xorg.conf.original-1
xorg.conf.original-2
xorg.conf.original-3

---

### Post by Hungry Man on 2013-08-02
Some of the graphical effects (like moving windows around) work again, which is interesting. And it's much faster. But it looks like compiz is still crashing/ not working.

---

### Post by Hungry Man on 2013-08-02
Bump.

---

### Post by QIII on 2013-08-02
Are you getting any error messages or the apport dialog?

---

### Post by Hungry Man on 2013-08-02
I think I uninstalled Apport a while back because it was incompatible with some software/ kept crashing. So no, no apport dialog or error messages.

---

### Post by Hungry Man on 2013-08-02
I think I uninstalled Apport a while back because it was incompatible with some software/ kept crashing. So no, no apport dialog or error messages.

edit: Double post, whoops.

---

