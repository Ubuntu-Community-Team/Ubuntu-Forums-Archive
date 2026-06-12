---
title: "No screensaver/screen lock after upgrading to Hardy"
date: 2008-06-06
forum: General Help
---

### Post by silywalks on 2008-06-06
Hello,

Apologies if there was a thread about this kind of problem recently, I've done a fair bit of searching and most of the screensaver-related threads were either non-related to my problem or concluded in a "hey, it fixed itself magically" type of post.

I've recently upgraded my system from Gutsy to Hardy. Some minor issues I solved myself, but there's one thing I can't figure out no matter how I try, and that is screensaver / screen locking / screen standby.

1. gnome-screensaver is not running by default (and I'm under impression it should). Gnome internals are black magic to me, so no idea how it should start.
2. 'Activate screensaver' from gnome-panel's locking app doesn't start it either.
3. After starting gnome-screensaver manually from a terminal, I can't lock my screen using gnome-panel locking app, and screensaver seems to be ignoring its settings (set through System -> Preferences -> Screensaver or through the locking app -> Properties). 
4. gnome-screensaver-command --lock from a terminal works fine (but is not particularly handy).
5. The display doesn't go to sleep either, even after specifying standby time in power management options.

Any hints would be much appreciated, no easy way of locking display and no screensaver/standby is really annoying...

---

### Post by lswest on 2008-06-06
if my memory serves me correctly do this: open a terminal and type ```
gconf-editor
``` go to apps-->gnome-screensaver and check "lock active" to be able to lock your screen when the screensaver is on.  Can you blank the screen or lock it after that?

---

### Post by silywalks on 2008-06-09
> **lswest said:**
> if my memory serves me correctly do this: open a terminal and type ```
gconf-editor
``` go to apps-->gnome-screensaver and check "lock active" to be able to lock your screen when the screensaver is on.  Can you blank the screen or lock it after that?

I assume you mean the 'lock-enabled' setting, and it's checked already. So is 'idle-activation-enabled'.

---

### Post by Forlong on 2008-06-09
What happens when running e.g. ```
/usr/lib/xscreensaver/glmatrix
``` in the terminal?

---

### Post by silywalks on 2008-06-09
It runs fine, in a window. Generally screensaver previews work, it's just that screensaver doesn't start, run nor lock on its own.

---

### Post by Forlong on 2008-06-09
Are you by any chance running Xgl?

---

### Post by silywalks on 2008-06-09
A tricky question; as I mentioned I don't know much about modern graphical environments. :) I don't have any Xgl packages installed, and the server is normal Xorg, if that answers your question.

I run compiz, if that changes anything (I'm aware there's a screensaver plugin for compiz, but as far as I know, its installation requires some effort so I'd rather use a packaged solution if possible).

---

### Post by Forlong on 2008-06-09
Only to make sure, run this and post the output here please: [http://ubuntuforums.org/showthread.php?t=799070](http://ubuntuforums.org/showthread.php?t=799070)

---

### Post by silywalks on 2008-06-09
Distribution:          Ubuntu 8.04
 Desktop environment:   GNOME
 Graphics chip:         nVidia Corporation GeForce 7300 GT (rev a2)
 Driver in use:         nvidia
 Rendering method:      Nvidia

Checking if it's possible to run Compiz on your system...

 Checking for texture_from_pixmap...               [ OK ]
 Checking for non power of two support...          [ OK ]
 Checking for composite extension...               [ OK ]
 Checking for FBConfig...                          [ OK ]
 Checking for hardware/setup problems...           [ OK ]

Update: As stupid as it seems, it looks like my problem 'magically' solved itself like those I mentioned in the opening post. Just noticed that both locking and the screensaver started to work properly. I don't recall reconfiguring or reinstalling anything related...

---

