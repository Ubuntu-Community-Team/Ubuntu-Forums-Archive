---
title: "Wine Okay?"
date: 2007-09-30
forum: General Help
---

### Post by Officer Dibble on 2007-09-30
I'm going to start experimenting with running the different Windows Programs that still make me slightly dependent on XP through Wine.

Is there any way that, just by trying to follow the basic and natural install route of a Windows program through Wine, that I can kill or seriously maim my treasured current Ubuntu setup?

Many thanks for your input. :)

---

### Post by Sisophon2001 on 2007-09-30
Yes wine is okay. It will not effect your existing set-up. Experiment away, but be aware that many programs are not supported. It may be better to goggle to see if the applications you wish to use will run well under wine before wasting time.

Garvan

---

### Post by az on 2007-09-30
> **Officer Dibble said:**
> I'm going to start experimenting with running the different Windows Programs that still make me slightly dependent on XP through Wine.

Is there any way that, just by trying to follow the basic and natural install route of a Windows program through Wine, that I can kill or seriously maim my treasured current Ubuntu setup?

Many thanks for your input. :)

I have never heard of it happening, but in theory, a well-crafted windows program could circumvent the protection buillt-into wine (which puts everything in folder in your home drive and makes the installed program think that's C:) and hose your whole home drive.  It should be fine, but I would not risk anything on a system that had irreplaceable files.

---

### Post by ajgreeny on 2007-09-30
If you try something with a big install that doesn't work, you can, as far as I'm aware, just delete the folder wine makes for that program in ~/.wine/drive_c/Program Files/folder_name.  There may be other files present as well in other places in the .wine folder but the main bulk will be in the named folder, and deleting that in my experience does no harm, but releases disk space if it is at a premium.

I did this with Lotus Smartsuite 97.  It would not work properly for Wordpro, though Lotus 123 did OK.  Anyway, attempts to uninstall were not successful either, so I just deleted the /Lotus folder made when I installed and have had no difficulties since.

---

