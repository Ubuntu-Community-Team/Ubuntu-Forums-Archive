---
title: "Ctrl-Fn key combination not working"
date: 2008-02-20
forum: General Help
---

### Post by tswd on 2008-02-20
I'm running Ubuntu 7.10 and using a Microsoft Natural keyboard.

I recently installed Intellij IDEA and wasn't happy with the performance under Gnome (my machine isn't real powerful). I decided to try a lighter desktop and installed xfce. When I tried to set a breakpoint in IDEA, which uses Ctrl-F8, nothing happens. I switched back over to Gnome and it worked fine.

Out of curiosity, I installed KDE and tried it. Same behavior as xfce, the ctrl-f8 combination doesn't work.

I tried xev under the different desktops and here's the output from xfce and KDE:

KeyPress event, serial 30, synthetic NO, window 0x2400001,
    root 0x82, subw 0x0, time 962837276, (169,-14), root:(720,394),
    state 0x0, keycode 74 (keysym 0xffc5, F8), same_screen YES,
    XLookupString gives 0 bytes: 
    XmbLookupString gives 0 bytes: 
    XFilterEvent returns: False

KeyRelease event, serial 30, synthetic NO, window 0x2400001,
    root 0x82, subw 0x0, time 962837363, (169,-14), root:(720,394),
    state 0x0, keycode 74 (keysym 0xffc5, F8), same_screen YES,
    XLookupString gives 0 bytes: 
    XFilterEvent returns: False

KeyPress event, serial 30, synthetic NO, window 0x2400001,
    root 0x82, subw 0x0, time 962838549, (169,-14), root:(720,394),
    state 0x0, keycode 37 (keysym 0xffe3, Control_L), same_screen YES,
    XLookupString gives 0 bytes: 
    XmbLookupString gives 0 bytes: 
    XFilterEvent returns: False

FocusOut event, serial 30, synthetic NO, window 0x2400001,
    mode NotifyGrab, detail NotifyAncestor

FocusIn event, serial 30, synthetic NO, window 0x2400001,
    mode NotifyUngrab, detail NotifyAncestor

KeymapNotify event, serial 30, synthetic NO, window 0x0,
    keys:  2   0   0   0   32  0   0   0   0   0   0   0   0   0   0   0   
           0   0   0   0   0   0   0   0   0   0   0   0   0   0   0   0   

KeyRelease event, serial 30, synthetic NO, window 0x2400001,
    root 0x82, subw 0x0, time 962840387, (169,-14), root:(720,394),
    state 0x4, keycode 37 (keysym 0xffe3, Control_L), same_screen YES,
    XLookupString gives 0 bytes: 
    XFilterEvent returns: False


When I run that under Gnome, I get a KeyPress event with a modified state instead of the KeymapNotify event. How do I get xfce and kde to behave normally?

Thanks,
Rich

---

### Post by tswd on 2008-02-21
OK, figured it out. For xfce, anyway. Had to go to the Window Manager settings, create a new keyboard profile, and remove the keybindings using the key combinations I needed.

---

