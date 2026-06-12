---
title: "Super key problems"
date: 2007-06-14
forum: General Help
---

### Post by emax on 2007-06-14
I've got a problem with my Super key under Feisty.

If I set a keyboard shortcut to use <Super> (example <Super>1 to move to workspace 1) and then simply press "1", it's as if I was also holding down the Super key as well.

Both GNOME and KDE exhibit this behaviour.

If I boot off the 7.04 install disk, I don't get this behaviour.

Using xev, I get the following output:

pressing Super on its own:

KeyPress event, serial 26, synthetic NO, window 0x2c00001,
    root 0x4d, subw 0x0, time 5054276, (415,96), root:(425,169),
    state 0x10, keycode 115 (keysym 0x0, NoSymbol), same_screen YES,
    XLookupString gives 0 bytes: 
    XmbLookupString gives 0 bytes: 
    XFilterEvent returns: False

KeyRelease event, serial 29, synthetic NO, window 0x2c00001,
    root 0x4d, subw 0x0, time 5054345, (415,96), root:(425,169),
    state 0x10, keycode 115 (keysym 0x0, NoSymbol), same_screen YES,
    XLookupString gives 0 bytes: 
    XFilterEvent returns: False

pressing "2" on its own:

KeyPress event, serial 29, synthetic NO, window 0x2c00001,
    root 0x4d, subw 0x0, time 5100703, (132,81), root:(142,154),
    state 0x10, keycode 11 (keysym 0x32, 2), same_screen YES,
    XLookupString gives 1 bytes: (32) "2"
    XmbLookupString gives 1 bytes: (32) "2"
    XFilterEvent returns: False

KeyRelease event, serial 29, synthetic NO, window 0x2c00001,
    root 0x4d, subw 0x0, time 5100803, (132,81), root:(142,154),
    state 0x10, keycode 11 (keysym 0x32, 2), same_screen YES,
    XLookupString gives 1 bytes: (32) "2"
    XFilterEvent returns: False

pressing <Super>2:

KeyPress event, serial 29, synthetic NO, window 0x2c00001,
    root 0x4d, subw 0x0, time 5140571, (94,144), root:(104,217),
    state 0x10, keycode 115 (keysym 0x0, NoSymbol), same_screen YES,
    XLookupString gives 0 bytes: 
    XmbLookupString gives 0 bytes: 
    XFilterEvent returns: False

KeyPress event, serial 29, synthetic NO, window 0x2c00001,
    root 0x4d, subw 0x0, time 5140737, (94,144), root:(104,217),
    state 0x10, keycode 11 (keysym 0x32, 2), same_screen YES,
    XLookupString gives 1 bytes: (32) "2"
    XmbLookupString gives 1 bytes: (32) "2"
    XFilterEvent returns: False

KeyRelease event, serial 29, synthetic NO, window 0x2c00001,
    root 0x4d, subw 0x0, time 5140854, (94,144), root:(104,217),
    state 0x10, keycode 11 (keysym 0x32, 2), same_screen YES,
    XLookupString gives 1 bytes: (32) "2"
    XFilterEvent returns: False

KeyRelease event, serial 29, synthetic NO, window 0x2c00001,
    root 0x4d, subw 0x0, time 5141252, (94,144), root:(104,217),
    state 0x10, keycode 115 (keysym 0x0, NoSymbol), same_screen YES,
    XLookupString gives 0 bytes: 
    XFilterEvent returns: False

I tried changing my keyboard type from "Generic 104-key PC" to Logitech Internet Keyboard and got the following error dialogue:

Error activating XKB configuration.
It can happen under various circumstances:
- a bug in libxklavier library
- a bug in X server (xkbcomp, xmodmap utilities)
- X server with incompatible libxkbfile implementation

X server version data:
The X.Org Foundation
70200000

If you report this situation as a bug, please include:
- The result of xprop -root | grep XKB
- The result of gconftool-2 -R /desktop/gnome/peripherals/keyboard/kbd

$ xprop -root | grep XKB
_XKB_RULES_NAMES_BACKUP(STRING) = "xorg", "pc104", "gb", "gb", ""
_XKB_RULES_NAMES(STRING) = "xorg", "pc104", "gb", "gb", ""

$ gconftool-2 -R /desktop/gnome/peripherals/keyboard/kbd
layouts = []
model = logiik
options = []
overrideSettings = true

Any ideas would be greatly appreciated.

---

### Post by Blayde on 2007-06-14
I have had this same problem with the super key and I just figured it wasn't setup to be used in that way. I hate to tell you 'Nothing to see here; Move along,' but wouldn't using Ctrl+Alt+Whatever work alright? I do have my fingers crossed that eventually the super key behaves like a modifier like shift, ctrl, and alt, but for now it seems to act like its own key.

---

### Post by emax on 2007-07-26
Thanks for the response but I'm still not 100% convinced Blayde.

If I boot up my machine off the 7.04 install media, the Super key behaves like I'd expect so it has to be some issue with the configuration somewhere, no?

---

