---
title: "Switch Control and Alt keys (both sides)"
date: 2007-07-07
forum: General Help
---

### Post by ThinkBuntu on 2007-07-07
To make it quick, here's my Xev output for both Control and Alt keys. I'd like to switch them on each side of the keyboard, because I want my Control key where I'm used to an Apple key being.
**Left Control**
```
KeyPress event, serial 32, synthetic NO, window 0x2c00001,
    root 0x3e, subw 0x0, time 8965037, (151,-16), root:(168,550),
    state 0x0, keycode 37 (keysym 0xffe3, Control_L), same_screen YES,
    XLookupString gives 0 bytes:
    XmbLookupString gives 0 bytes:
    XFilterEvent returns: False

KeyRelease event, serial 32, synthetic NO, window 0x2c00001,
    root 0x3e, subw 0x0, time 8965140, (151,-16), root:(168,550),
    state 0x4, keycode 37 (keysym 0xffe3, Control_L), same_screen YES,
    XLookupString gives 0 bytes:
    XFilterEvent returns: False
```
**Left Alt**
```
KeyPress event, serial 32, synthetic NO, window 0x2c00001,
    root 0x3e, subw 0x0, time 9001470, (116,-5), root:(133,561),
    state 0x0, keycode 64 (keysym 0xffe9, Alt_L), same_screen YES,
    XLookupString gives 0 bytes:
    XmbLookupString gives 0 bytes:
    XFilterEvent returns: False

KeyRelease event, serial 32, synthetic NO, window 0x2c00001,
    root 0x3e, subw 0x0, time 9001549, (116,-5), root:(133,561),
    state 0x8, keycode 64 (keysym 0xffe9, Alt_L), same_screen YES,
    XLookupString gives 0 bytes:
    XFilterEvent returns: False
```
**Right Control**
```
KeyPress event, serial 32, synthetic NO, window 0x2c00001,
    root 0x3e, subw 0x0, time 9050249, (144,-11), root:(161,555),
    state 0x0, keycode 113 (keysym 0xffea, Alt_R), same_screen YES,
    XLookupString gives 0 bytes:
    XmbLookupString gives 0 bytes:
    XFilterEvent returns: False

KeyRelease event, serial 32, synthetic NO, window 0x2c00001,
    root 0x3e, subw 0x0, time 9050312, (144,-11), root:(161,555),
    state 0x8, keycode 113 (keysym 0xffea, Alt_R), same_screen YES,
    XLookupString gives 0 bytes:
    XFilterEvent returns: False
```
**Right Alt**
```
KeyPress event, serial 32, synthetic NO, window 0x2c00001,
    root 0x3e, subw 0x0, time 9053048, (271,-75), root:(288,491),
    state 0x0, keycode 109 (keysym 0xffe4, Control_R), same_screen YES,
    XLookupString gives 0 bytes:
    XmbLookupString gives 0 bytes:
    XFilterEvent returns: False

KeyRelease event, serial 32, synthetic NO, window 0x2c00001,
    root 0x3e, subw 0x0, time 9053111, (271,-75), root:(288,491),
    state 0x4, keycode 109 (keysym 0xffe4, Control_R), same_screen YES,
    XLookupString gives 0 bytes:
    XFilterEvent returns: False
```
So, how do I pull this off?

---

### Post by ThinkBuntu on 2007-07-07
Note: I am able to successfully unmap and remap my Control keys, but don't know what Alt's modifier is. Here are my commands so far, with the missing ones noted.
```
$ xmodmap -e "remove Control = Control_L"
$ xmodmap -e "remove Control = Control_R"
$ # missing command to unmap Alt_L
$ # missing command to unmap Alt_R
$ xmodmap -e "keycode 64 = Control_L"
$ xmodmap -e "keycode 109 = Control_R"
$ xmodmap -e "keycode 37 = Alt_L"
$ xmodmap -e "keycode 113 = Alt_R"
$ xmodmap -e "add Control = Control_L"
$ xmodmap -e "add Control = Control_R"
$ # missing command to add Alt_L
$ # missing command to add Alt_R

```

---

### Post by ThinkBuntu on 2007-07-07
Well, I was able to fix it. It wouldn't load, even as an executable ~/.xmodmap file, but I saved it as a shell script that runs with every new session. Here's my final code, for anyone interested:
```
xmodmap -e "remove Control = Control_L";
xmodmap -e "remove Control = Control_R";
xmodmap -e "remove Mod1 = Alt_L";
xmodmap -e "remove Mod1 = Alt_R";
xmodmap -e "keycode 64 = Control_L";
xmodmap -e "keycode 109 = Control_R";
xmodmap -e "keycode 37 = Alt_L";
xmodmap -e "keycode 113 = Alt_R";
xmodmap -e "add Control = Control_L";
xmodmap -e "add Control = Control_R";
xmodmap -e "add Mod1 = Alt_L";
xmodmap -e "add Mod1 = Alt_R";
```

---

### Post by n6k6t6 on 2008-02-27
I swapped Control and Alt keys by creating a file called ~/.xmodmap.
Here is my ~./xmodmap:

clear control
clear mod1
keycode 64 = Control_L
keycode 37= Alt_L
keycode 109 = Alt_R
keycode 113 = Control_R
add control = Control_L Control_R
add mod1 =  Alt_L Alt_R

You can figure out the keycodes by running xev

---

