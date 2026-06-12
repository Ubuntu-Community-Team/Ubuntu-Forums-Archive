---
title: "Before giving up... Ati mobility x1600 and enabling vsync"
date: 2007-10-08
forum: General Help
---

### Post by Batuhan on 2007-10-08
I've read almost every single topic about it and still could not manage to do it.

Vsync with this card just does not work. I get image tearing problems when moving videos or playing videos(small artifacts) and I sometimes do openGL visuals stuff and it becomes very annoying then.

I have the latest ati drivers.

Without XGL and CF, there is this tearing problem and I write to console:

```
sudo aticonfig --vs=on
```

It writes to my xorg.conf but does not make a difference.

I install XGL and compiz fusion, and the problem is still there. From compiz settings, I flip "Sync to vsync" option, I play with it's refresh rate and stuff but basically nothing works. I still get the horizontal tearing effect.

This happens while dragging windows, during openGL use, or videos. Most people would not consider this as a problem but I do.

Anyone managed to enable vsync with this graphics card?
I'm checking my xorg logs and it looks like it is enaling vsync without problems... But it does not work for some reason.

In a thread I've seen someone saying that the problem is gone with driver v8.39.4 and came back with a newer version. Maybe I should try going back to that driver but I use Envy to update my drivers and don't know how to install that one manually. I tried once, generated a package for Buntu and installed but it fell back to mesa complaining about the fglrx kernel module version mismatch.

If nothing helps I'd like to try do go back to that driver to see how it works but someone should point me to the directions of installing the ATI display driver manually from ATI website. I actually install it form there but I need to see the additional steps for updating the kernel modules and such...

---

### Post by madneon on 2008-04-11
**This post could be related to an Ubuntu bug filed at**: 214154 [br].[/br] ---------------------------- [br].[/br] [br].[/br]
				Same problem with ATI Mobility Radeon HD 2600 XT.

Tearing effect looks just terrible.
...need a solution :/

---

