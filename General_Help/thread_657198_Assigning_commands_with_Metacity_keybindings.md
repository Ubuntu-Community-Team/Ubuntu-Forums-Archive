---
title: "Assigning commands with Metacity keybindings"
date: 2008-01-03
forum: General Help
---

### Post by FuturePilot on 2008-01-03
I have a Search key on my keyboard and currently when I press it, it brings up the default search dialog. However I would like it to open Tracker Search Tool instead. I found a way you can do this with the Metacity keybindings in gonf-editor. However I'm not exactly sure how to map the command to this particular key. Anyone know how to do this?

---

### Post by p_quarles on 2008-01-03
You can get the system names of keys by using "xev." I can't remember whether it's installed by default, but it's definitely in the main repository. 

Anyway, type the command (xev) in a terminal. You'll see a new window open up, but this is only useful for ending the process. Once it's open, press a key, and the terminal will give you verbose information about the "X event" that corresponds to that key.

---

### Post by FuturePilot on 2008-01-03
Here is the output from xev. 
```
KeyPress event, serial 31, synthetic NO, window 0x3800001,
    root 0x1a5, subw 0x0, time 1085747618, (-52,247), root:(619,298),
    state 0x10, keycode 229 (keysym 0x0, NoSymbol), same_screen YES,
    XLookupString gives 0 bytes: 
    XmbLookupString gives 0 bytes: 
    XFilterEvent returns: False

KeyRelease event, serial 31, synthetic NO, window 0x3800001,
    root 0x1a5, subw 0x0, time 1085747618, (-52,247), root:(619,298),
    state 0x10, keycode 229 (keysym 0x0, NoSymbol), same_screen YES,
    XLookupString gives 0 bytes: 
    XFilterEvent returns: False

```
What is the information that I would need?

---

### Post by p_quarles on 2008-01-03
It looks like it's saying the key is called "NoSymbol." Do you have other extended media keys? I'm just curious if you get the same results with any other keys.

---

### Post by FuturePilot on 2008-01-03
Yes, here's what I got from the Play key
```
FocusOut event, serial 31, synthetic NO, window 0x3800001,
    mode NotifyGrab, detail NotifyAncestor

FocusIn event, serial 31, synthetic NO, window 0x3800001,
    mode NotifyUngrab, detail NotifyAncestor

KeymapNotify event, serial 31, synthetic NO, window 0x0,
    keys:  2   0   0   0   0   0   0   0   0   0   0   0   0   0   0   0   
           0   0   0   0   0   0   0   0   0   0   0   0   0   0   0   0   

```
and the Back key
```
FocusOut event, serial 31, synthetic NO, window 0x3800001,
    mode NotifyGrab, detail NotifyAncestor

FocusIn event, serial 31, synthetic NO, window 0x3800001,
    mode NotifyUngrab, detail NotifyAncestor

KeymapNotify event, serial 31, synthetic NO, window 0x0,
    keys:  2   0   0   0   0   0   0   0   0   0   0   0   0   0   0   0   
           0   0   0   0   0   0   0   0   0   0   0   0   0   0   0   0   

```

---

### Post by p_quarles on 2008-01-03
Hmm. Not entirely certain how to interpret those. In any case, try binding Tracker to the key called "NoSymbol" and see if that happens to work. 

If not, I'm guessing there must be some way of binding a command to the keycode (229) instead of the name.

---

### Post by FuturePilot on 2008-01-03
I tried assigning it to "NoSymbol" but it didn't work. I was thinking of looking into the keycode 229 next. Thanks for your help by the way. ;)

---

### Post by p_quarles on 2008-01-03
Sure thing. 

You might actually want to look at the "keylaunch" package as well. I think xev might be more useful to those of us who use text-configured window managers (Fluxbox, in my case). Gnome's GUIfication might make it overly complicated to try to map an X event directly onto a command. I don't know, tbh.

---

