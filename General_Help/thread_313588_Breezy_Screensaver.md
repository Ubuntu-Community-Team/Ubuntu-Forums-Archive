---
title: "Breezy Screensaver?"
date: 2006-12-06
forum: General Help
---

### Post by twoseids on 2006-12-06
Whatever happened to the cool screensavers on Breezy when Dapper came out? I wish I could get those screensavers back, cuz the ones that came with Dapper are kind of lame.

This may have been addressed already somewhere else, but I've been unable to find it. Thanks for your help!

---

### Post by deadgobby on 2006-12-06
Did you peep into Synaptic?
 Gobby

---

### Post by twoseids on 2006-12-06
> **deadgobby said:**
> Did you peep into Synaptic?
 Gobby
Yes. I have xscreensaver and gnome-screensaver. I don't know what the Breezy default screensavers were called. But maybe this isn't a Breezy-Dapper thing - maybe it has something to do with the newer version of Gnome?

---

### Post by CatKiller on 2006-12-06
There was a change from xscreensaver to gnome-screensaver with Breezy->Dapper. Depending on how you installed, you might not have the extra packages.

You might want to install some or all of 
[B]xscreensaver-data
xscreensaver-data-extra
xscreensaver-gl
xscreensaver-gl-extra[/B]

The extra packages are in the Universe repository. They're all installable through Synaptic, as deadgobby says.

---

### Post by twoseids on 2006-12-06
> **CatKiller said:**
> There was a change from xscreensaver to gnome-screensaver with Breezy->Dapper. Depending on how you installed, you might not have the extra packages.

You might want to install some or all of 
[B]xscreensaver-data
xscreensaver-data-extra
xscreensaver-gl
xscreensaver-gl-extra[/B]

The extra packages are in the Universe repository. They're all installable through Synaptic, as deadgobby says.
Yes! That did the trick. Thank you!

---

### Post by twoseids on 2006-12-11
Okay, now I have a follow-up question. Where are the image files used for the screensaver? It used to be that my favorite ones, Zoom and Spotlight, used whatever was on the current screen as the "background" image. But now, Zoom uses something which I can't even identify and Spotlight uses (I think) images from the Cosmos screensaver.

Where are all these images? And how could I change my Screensaver settings to have different images appear?

---

### Post by richi on 2007-08-15
On my Ubuntu Feisty, Cosmos images are located in /usr/share/pixmaps/backgrounds/cosmos/. You can add your own if you wish. Pre-installed images are 1200x800 jpegs, but you can also use other formats (e.g. png) and dimensions if you wish (Cosmos won't automatically scale them to fit your screen, though).

You can find space images in sites like [http://www.wwu.edu/depts/skywise/wallpaper.html]("http://www.wwu.edu/depts/skywise/wallpaper.html") or [http://hubblesite.org/gallery/wallpaper/]("http://hubblesite.org/gallery/wallpaper/"), among many others.

Richard

---

