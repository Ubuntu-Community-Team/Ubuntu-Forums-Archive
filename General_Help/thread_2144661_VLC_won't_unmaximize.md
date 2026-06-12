---
title: "VLC won't unmaximize"
date: 2013-05-13
forum: General Help
---

### Post by baillou2 on 2013-05-13
So I was watching a video on VLC and switched it to full screen mode via alt then typing full screen. Once it switched though I couldn't get it back to any other size. None of the regular buttons worked. No alt, No super key. Nothing. My only option was to use alt+f4 which did work.

Now my problem is I can't get the player back to normal because whenever I start it up it reloads in full screen mode. I guess I'll have to uninstall it and re-install it.

Any idea of what this bug is? Has anyone else had this problem? It's really annoying.

---

### Post by deadflowr on 2013-05-13
I thought the default toggle for full screen was F11.

alt + F4 just closes the current window.

And the super key toggles the dash/launcher functions.

Hold down the super key to see more keyboard shortcuts.

---

### Post by andrew.46 on 2013-05-13
For me the f key goes fullscreen and esc returns. For all the default keys have a look at Tools --> Preferences --> Hotkeys.

---

### Post by baillou2 on 2013-05-13
That's the problem. F11 doesn't work. 
alt+f4 does though. So I can at least close it.

---

### Post by philinux on 2013-05-13
> **baillou2 said:**
> That's the problem. F11 doesn't work. 
alt+f4 does though. So I can at least close it.

Delete it's config files.

/home/user/.config/vlc
/home/user/.cache/vlc
/home/user/.local/share/vlc

---

