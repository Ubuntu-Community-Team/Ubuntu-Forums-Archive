---
title: "Odd keyboard malfuntion with beryl"
date: 2006-11-13
forum: General Help
---

### Post by Azakus on 2006-11-13
Hi all. I just installed beryl with xgl and have gnome-settings-daemon starting up with it. I noticed that after the install, I can no longer use the "." button on my keyboard's num pad. How can I fix this?

---

### Post by Azakus on 2006-11-14
Bump

---

### Post by Ramaddan on 2006-11-14
Hi,
This is an XGL issue.
I managed to get AIGLX going with ATI drivers installed, and there were no keyboard issues or conflicts, but ATI drivers do not come with composite support, thus direct rendering was wacky in some cases, or disfunctional in others, so I went back to not using Beryl, till ATI starts supporting the composite at least.

I did not want to use XGL also, because of the keyboard issues, so I'm just hoping ATI will put composite support soon in their drivers, then I will be able to fully use AIGLX, because it's much better, with no conflicts or side effects, since it is part of the desktop as a module, rather than a manager on its own top of the desktop.

I know this does not help your problem, but I thought to at least tell you so as to save you much hard ship, and frustration.

If anyone has a fix for XGL, it would be great, but I don't know of any yet.

If you don't use ATI, then you can take a look on whether on graphic card supports AIGLX.
I think nVidia does.

NOTE: The open source drivers that come with the xserver support direct rendering with some ATI graphics card, but they don't seem to support mine, ATI Radeon 9600XT. And the ATI official drivers (fglrx) do not support AIGLX yet.

---

