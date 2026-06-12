---
title: "Ubuntu in VMWare"
date: 2006-07-03
forum: General Help
---

### Post by mejy on 2006-07-03
I cannot run Ubuntu on my primary desktop since I simply cannot get my network card to work (its a Home PNA card so its not simmply a case of 'get another one', and the router cannot be located near enough to the PC for ethernet).  For the time being, I've been forced back to windows but still want the ability to run Ubuntu under VMWare.

Unfortunately, I get horrible graphical perofrmance.  GLXGears clames around 500 FPS, despite the grears clearly moving around at no more than about 4 fps on average.  This on its own I could cope with, but I get the same sort of responsiveness when dragging windows etc and other parts of the UI which makes it impossible to use for extended periods.  The mouse, on the other hand, moves fine.

The host os is windows xp, with an AMD 4800+ and a nVidia 7800 gt, so I can't believe its a raw performance issue.  VMWare tools is installed.

Does anyone know what could be causing these problems?

---

### Post by hda on 2006-07-03
I don't think you can use the full performance of your graphics adapter under VMware, so you're better off with a dual boot system. Reserving 16 GB for a Linux partition on today's hard drive isn't really an issue.

On the other hand I can *work* perfectly with only 500 fps on glxgears (this is NOT a benchmark!) on my ubuntu system. No gaming needed.

---

### Post by mejy on 2006-07-03
[QUOTE=hda]I don't think you can use the full performance of your graphics adapter under VMware, so you're better off with a dual boot system. Reserving 16 GB for a Linux partition on today's hard drive isn't really an issue.

On the other hand I can *work* perfectly with only 500 fps on glxgears (this is NOT a benchmark!) on my ubuntu system. No gaming needed.[/QUOTE]

As I mentioned, I can't run Ubuntu on the system with the current state of drivers, so was hoping to run it in VMWare temporarily untill i can get this sorted.  I'm not looking for gaming, XGL or anything else requiring acceleration, just a reasonably responsive system.

The main problem is with metacity windows - even with wire frames turned on they move ridiculously slowly (and, actually, no faster than with wire frames turned off).  I mentioned the glxgears issue out of hope that this might be related.

This aside, I'm surprised with how rquick everything else is.

---

