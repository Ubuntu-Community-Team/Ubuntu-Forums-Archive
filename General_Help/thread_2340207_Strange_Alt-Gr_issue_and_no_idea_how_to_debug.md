---
title: "Strange Alt-Gr issue and no idea how to debug"
date: 2016-10-16
forum: General Help
---

### Post by JosefCS on 2016-10-16
Hi,

I am hoping to get directions on how to approach finding the source of the error in order to resolve this or get a bug report for the fitting software part.

Using ubuntu 16.04 in german with a german keyboard.

Note, this is seems not to be related to the used editors (vim, neovim), but rather these editors are affected by the below mentioned behavior.

A while ago, when typing in neovim in gnome-terminal, normally I was able to type a command, like "ct<alt-gr>\" and the command works as expected.
Then, a strange error occured, where the key "<alt-gr>" cleared the previous commands in neovim (i.e. it would act as if <ESC> was pressed and the "ct" was cleared).
Originally, I thought this was a bug in neovim, but it quickly turned out to happen in vim too.
I could not locate the source for this error, but everything worked fine on my other machines. After a reinstall, the behavior went away.

Unfortunately, the error occured again, in the middle of my work. I was in the terminal, switched windows, opened a new tab in chrome and switched back to the console and the dreaded error occured again.

It occurs in any console opened (xterm, rxvt, gnome-terminal). When I press the <alt-gr> key in the terminal, the cursor flickers once very shortly, which it doesn't on my other, working systems.

The only difference was in xev a KeymapNotify which seems not to occur on the other systems:

```

KeymapNotify event, serial 37, synthetic NO, window 0x0,
    keys:  4294967227 0   0   0   0   0   0   0   0   0   0   0   0   16  0   0   
           0   0   0   0   0   0   0   0   0   0   0   0   0   0   0   0   


KeyPress event, serial 37, synthetic NO, window 0x2a00001,
    root 0x1e8, subw 0x0, time 101992705, (-197,674), root:(1507,726),
    state 0x0, keycode 108 (keysym 0xfe03, ISO_Level3_Shift), same_screen YES,
    XKeysymToKeycode returns keycode: 92
    XLookupString gives 0 bytes: 
    XmbLookupString gives 0 bytes: 
    XFilterEvent returns: False


KeyRelease event, serial 37, synthetic NO, window 0x2a00001,
    root 0x1e8, subw 0x0, time 101995137, (-197,674), root:(1507,726),
    state 0x80, keycode 108 (keysym 0xfe03, ISO_Level3_Shift), same_screen YES,
    XKeysymToKeycode returns keycode: 92
    XLookupString gives 0 bytes: 
    XFilterEvent returns: False




```

Does anybody have an idea on how to proceed further?


Thank you,
Josef

---

