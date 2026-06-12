---
title: "Create desktop overlay"
date: 2016-07-31
forum: General Help
---

### Post by chris137 on 2016-07-31
Hi,

I'd like to create a desktop overlay (showing the current time) to be shown above a fullscreen VLC window (which is focused).

I tried using conky which I use for different stuff and got pretty close to what I want.
Unfortunately it still is behind VLC's fullscreen (F11) which is my only use case for this.

How would I go about that?
I could not find any overlay-software for this.

---

### Post by CatKiller on 2016-08-01
You may already have tried these, and VLC's fullscreen might override them anyway, but you could try either the own_window_type = 'dock' or own_window_hints = 'undecorated,above,sticky,skip_taskbar,skip_pager' conky settings to get the behaviour you want out of conky. Note you can only use one or the other; if you use _type, _hints is ignored.

You might also be able to use devilspie to force one window to be above the other regardless of what they would do otherwise.

---

### Post by chris137 on 2016-08-01
This got me pretty close but I'm still not quite there.
devilspie allows me to get conky above vlc, however for this I have to put vlc in the background. Doing this results in the GNOME panel appearing on top (just like when vlc loses focus) which I don't want.
This also is an annoying behavior.
I tried to figure out if I can disable the panel on that monitor since I don't need it on that one anyways but could not find a solution. Just this bug which seems to address this:
[https://bugs.launchpad.net/unity/+bug/853865](https://bugs.launchpad.net/unity/+bug/853865)

---

### Post by CatKiller on 2016-08-01
I can't remember which particular combination of Ctrl, Alt & Super you need to press to get the right-click menu on the panel - they seemed to add another button every release for a while - but then it's just Delete This Panel to remove it.

---

### Post by chris137 on 2016-08-01
I also encountered this.
I could not find any way to make an options-menu appear in the panel
No combination of Ctrl, Alt, Super and right click does anything for me.

---

### Post by CatKiller on 2016-08-01
Alt-Super-rightclick.

---

### Post by chris137 on 2016-08-01
Nope, unfortunately nothing happens there.
I also switched from having my window's menu there to having it in their own title bar but that doesn't seem to have any effect on this.

As far as I could figure out I'm running GNOME 2. Does your solution maybe apply to GNOME 3 only?

---

### Post by CatKiller on 2016-08-01
Alt-Gr is not the same as Alt.

---

### Post by chris137 on 2016-08-01
Yes, I'm aware.
Neither are working.

---

### Post by CatKiller on 2016-08-02
I don't know what to tell you. It used to be simply right-clicking on an empty part of the panel (I assume you've tried that already?), then it was Alt-click, then it was Alt-left Super-click. IIRC, this happened in Ubuntu's Gnome 2 around the time that Unity happened, and persisted into Gnome 3. I'm not aware of any distros that use a vanilla Gnome 2 these days, but there are derivatives like Mate and Cinnamon. If you're using one of those, they probably have their own method.

---

### Post by chris137 on 2016-08-02
Well thanks for your help so far but I don't know what to tell you either.
Right-clicking gives me either the focused window's menu (meaning resize, move, always on top and close) or nothing if the desktop is focused.

I might have given some wrong information since desktops aren't really my specialty but I wouldn't know what.

---

### Post by CatKiller on 2016-08-02
That's peculiar. Right-clicking on the desktop should give you the desktop menu. And it's clicking on the panel that you want if you still want to delete the panel. Specifically, a bare patch of the panel; if you've got Unity's stupid window menu on the panel thing going on, you'll want to avoid that area entirely. You'll also want to not do it if you've also got your fullscreen window. That's likely to mess all sorts of things up.

As a completely sideways option, most of the desktop environments have some kind of internal OSD machinery for their own notifications and suchlike. You may be able to co-opt that in some fashion to get the overlay you want. I have no idea how any of them work, though.

Also, you might be able to also set the panel to be below using devilspie and let the panel and VLC fight over who gets the bottom bunk.

---

