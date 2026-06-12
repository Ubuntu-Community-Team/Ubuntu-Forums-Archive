---
title: "Why do I need to restart my system?"
date: 2008-07-10
forum: General Help
---

### Post by memories on 2008-07-10
I don't understand why I need to restart my system after doing certain things? This was never an issue in any other distro I tried. 

Unless I'm installing a new kernel, wouldn't reloading the mod or something suffice? 

How do I get rid of the You Need To Restart icon in my tray? I can't/don't want to reboot, ever, unless there's a kernel update.

---

### Post by Dr Small on 2008-07-10
You shouldn't have to, unless you installed video drivers or kernel updates, as far as I know. But, does it disappear if you reboot?

---

### Post by jualin on 2008-07-10
If you install a fix for a certain kernel or new video cards drivers for an Nvidia card you need to restart your system. At least that's my experience so far. With any other update I don't get the "Restart your system" message.

---

### Post by tribaal on 2008-07-10
Normally this icon appears precisely when you update/upgrade the kernel.

I noticed sometimes it also appears when updating modules. If you're technically savvy enough, it will have the exact same effect than modprobing the affeccted modules.
My wild guess is that since Ubuntu is targeted at a wider crowd than other distros, devs might have simply considered it was easier to let the average Joe reboot instead of risking (modules) dependency hell.

I'm not sure how you can manually get rid of the "restart" icon...

- Trib'

---

### Post by Ramses de Norre on 2008-07-10
Not even with drivers, you just reload the kernel modules. Ubuntu is a distro that should work for people with very little linux knowledge too, so telling such people to reload a kernel module is, well, not done. That's why ubuntu tells you to reboot, but if you know you don't, then don't :)

---

### Post by sdennie on 2008-07-10
You should be able to get rid of the reboot icon in the panel by going to System->Preferences->Sessions and turning off the Update Notifier.  You'll have to either kill that process (not positive what it's called) or logoff/login before the change takes effect.  Also, this will prevent you from getting notifications when updates are available so you'll have to run update-manager manually on occasion.

---

### Post by memories on 2008-07-10
I don't mind the icon, I understand that this is more user-friendly, but I would prefer if I was able to disable it or at least close this without having to kill it. 

I just disabled and then re-enabled one driver a second later (to restart it), and the icon hasn't went away, even though the driver is enabled and works fine. 

As for updates, I don't mind that so much.. I'd prefer just something like libnotify, a small bubble that just comes up and tells me there's an update, instead of the red arrow remaining there forever when there's updates I don't want to install. 

It sort of ruins the whole point of the red arrow. Since there are always updates I don't need, when there *are* important updates, I miss them because nothing changes, no new notifications, etc.

---

### Post by avtolle on 2008-07-10
The red arrow is to signal security updates; for normal updates, it is an orangish cog. Until all security updates are installed, there will be the red arrow, to the best of my knowledge.

---

