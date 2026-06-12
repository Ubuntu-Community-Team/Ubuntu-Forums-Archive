---
title: "Getting icons to appear in a Compiz theme"
date: 2008-05-25
forum: General Help
---

### Post by Brightbelt on 2008-05-25
Hi, I'm on Hardy and an intel Mac, and I've*_ finally_* gotten to where I am able to install emerald themes - mostly for the window effect, although there are, as always, some packages that won't install etc...

I am downloading themes from [www.gnome-look.org](www.gnome-look.org) and these themes seem to have such cool icons with them but I never see them install with the themes.

Is there a separate step I am missing to get the icons to install? I only finally got Compiz going after installing Fusion Icon in Synaptic.

I appreciate any guidance or help on this,
Many Thanks, Frank B.

---

### Post by Forlong on 2008-05-25
Themes and icons are simply different parts.

Just look out for a comment by the author regarding the icon set he/she used in the screenshot.

---

### Post by Brightbelt on 2008-05-25
Yes, I see, but can you give me specific understanding about where in the gnome interface and how I would go about installing icons?

There are many separate icon themes on the gnome-look site and I can download them. How one is to install them is pretty unclear to me.

And not to contradict you on purpose, but I have rarely, if ever, seen any separate comments by the author about installing icons with a compiz theme. Maybe I'm not looking in the right areas. 

I appreciate any specific help on these matters,...
Many Thanks, Frank B.

---

### Post by Brightbelt on 2008-05-25
I do now see in the gnome area (System/Preferences/Appearance/Icons) where I can get icons to install, but I'm still unsure about whether this works with Compiz or is a separate thing altogether.

Many Thanks, Frank B.

---

### Post by Forlong on 2008-05-25
> **Brightbelt said:**
> Yes, I see, but can you give me specific understanding about where in the gnome interface and how I would go about installing icons?

There are many separate icon themes on the gnome-look site and I can download them. How one is to install them is pretty unclear to me.
Just drag&drop the tarball into the "Appearance Preferences" window.
There's also the Install button on the lower right corner.
> **Brightbelt said:**
> And not to contradict you on purpose, but I have rarely, if ever, seen any separate comments by the author about installing icons with a compiz theme. Maybe I'm not looking in the right areas.
No, I did not meant that a comment regarding this is always there.
If the author didn't mention the icon set he/she used in the screenshot to show off his/her theme, it's simply rude behaviour (towards the creator of the icons as well as the user).

---

### Post by Forlong on 2008-05-25
> **Brightbelt said:**
> I do now see in the gnome area (System/Preferences/Appearance/Icons) where I can get icons to install, but I'm still unsure about whether this works with Compiz or is a separate thing altogether.
Compiz is just a window manager, that means it does not take care of any themes at all.

The desktop environment you are using is GNOME. That takes care of icons and themes.

The only thing the window manager is responsible for, are the window boarders. If you are not running Compiz, then Metacity (GNOME's default window manager) takes care of this,.
If you do use Compiz, then this gets handled by either gtk-window-decorator (that one just "clones" the one's from Metacity) or Emerald.

---

### Post by sayakb on 2008-05-25
You might as well extract and copy the icons to /usr/share/icons (But do open Nautilus as root)

---

### Post by Brightbelt on 2008-05-25
Many Thanks Forlong. I understand.

---

