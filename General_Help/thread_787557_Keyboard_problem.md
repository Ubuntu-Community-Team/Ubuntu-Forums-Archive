---
title: "Keyboard problem"
date: 2008-05-09
forum: General Help
---

### Post by PaoloRicardo on 2008-05-09
I can't get the pipe (vertical line) when using Ubuntu. It's OK in Windows with the US English layout but I lose it in Ubuntu, which makes using the command line a bit difficult!

Any solutions?

---

### Post by amohanty on 2008-05-09
From a terminal fire up xev:

xev

Now simply type out Shift+\ (or the pipe character).

If you dont see something like:

KeyPress event, serial 29, synthetic NO, window 0x1e00001,
    root 0x5a, subw 0x0, time 1947164, (742,646), root:(746,669),
    state 0x1, keycode 51 (keysym 0x7c, bar), same_screen YES,
    XLookupString gives 1 bytes: (7c) "|"
    XmbLookupString gives 1 bytes: (7c) "|"
    XFilterEvent returns: False

KeyRelease event, serial 29, synthetic NO, window 0x1e00001,
    root 0x5a, subw 0x0, time 1947244, (742,646), root:(746,669),
    state 0x1, keycode 51 (keysym 0x7c, bar), same_screen YES,
    XLookupString gives 1 bytes: (7c) "|"
    XFilterEvent returns: False

that means X is not getting the keycode from the keyboard. It is possible that your keyboard is kaput.

AM

---

### Post by PaoloRicardo on 2008-05-09
Hi am: the keyboard works fine under Windows so it can't be kaput, if you mean useless/hosed, and all key depressions give the expected result.

It doesn't work under Ubuntu i.e. the expected result does not appear after a key depression. For example if I press # I get £, if I press @ I get " (I can press " if I want @, of course), but there does not seem any way of getting pipe. I certainly don't get the pipe symbol when I press shift+| (I'm typing this under Windows so the symbol is there).

---

### Post by amohanty on 2008-05-09
Ok fire up the keyboard options window:
System->Preferences->Keyboard
Click on the Layouts tab and make sure the default layout is the right one. 
I think the default hardy install setups the keyboard switch applet that switches layout via a hotkey. Unfortunately I have dumped gdm/gnome for slim/openbox so dont have access to the relevant hotkey right now, but you can look for the applet in the panel and right click to setup options.

HTH
AM

---

### Post by PaoloRicardo on 2008-05-09
AM: thanks, changing the keyboard to USA solved the problem.

---

