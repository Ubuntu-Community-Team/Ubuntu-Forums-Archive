---
title: "dead-spacebar-on-kbd"
date: 2007-03-07
forum: General Help
---

### Post by ubu fubar on 2007-03-07
help!

On-log-in-today-the-space-bar-on-my-Thinkpad-t30-no-longer-works!

Nothing-has-changed-since-yesterday-in-terms-of-configuration,-no-new-stuff-installed-or-anything.

xev-shows-the-keypress-is-recognized,-but-there's-no-output:

```

KeyPress event, serial 26, synthetic NO, window 0x3400001,
    root 0x4d, subw 0x0, time 760105632, (289,338), root:(294,382),
    state 0x0, keycode 65 (keysym 0x1008ff15, XF86AudioStop), same_screen YES,
    XLookupString gives 0 bytes: 
    XmbLookupString gives 0 bytes: 
    XFilterEvent returns: False

KeyRelease event, serial 29, synthetic NO, window 0x3400001,
    root 0x4d, subw 0x0, time 760105735, (289,338), root:(294,382),
    state 0x0, keycode 65 (keysym 0x1008ff15, XF86AudioStop), same_screen YES,
    XLookupString gives 0 bytes: 
    XFilterEvent returns: False

```

Any-idea-how-I-can-get-it-back?

I've-tried-logging-out,-restarting-the-machine-etc.-to-no-avail.

---

### Post by ubu fubar on 2007-03-07
Update:

It-works-fine-when-logged-in-as-another-user,
so-it-must-be-related-to-my-profile...

---

### Post by Arisna on 2007-03-07
The only thing I can think of is to examine the file .xmodmap (note the preceding .) in your home folder.

---

### Post by ubu fubar on 2007-03-07
thanks,-contents-of-.Xmodmap:

```

keycode 234 = F19
keycode 233 = F20

```

F19+F20-are-the-browser-back/forward-keys

---

### Post by ubu fubar on 2007-03-07
Ok, I fixed it by resetting the keyboard layout to the defaults in System -> Keyboard -> Keyboard Layouts, which is strange as I have never changed the layout since installing the system 2 months ago.

As I was doing so, I had the Gconf window open in the background, at desktop / gnome / peripherals / keyboard / kbd, and noticed the settings there got wiped. The same / keyboard section has a subsection kbd.sysbackup which was wiped at the same time. I have no idea how these config options got populated in the first place, or even why as the kbd works fine without them.

Bizarre...

---

