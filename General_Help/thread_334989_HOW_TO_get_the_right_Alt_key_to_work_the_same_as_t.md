---
title: "HOW TO: get the right Alt key to work the same as the left in Gnome"
date: 2007-01-09
forum: General Help
---

### Post by Patrick K on 2007-01-09
In stock form Ubuntu (Gnome) comes with the right side Alt ket bound to AltGr which, so I have read, is for typing special characters. Many of us have no need for this and would like the right key to work the same as the left Alt key. 

To fix this go to  [System-Preferences] and open the Keyboard applet. Click on the Layout Options tab and "Alt/Win key behavior" then check "Alt and Meta are on the Alt key (Default)". Why it says default, I don't know. After that the right Alt key works the same as the left one.

This doesn't change the key's behavior in the Console, though. I don't know how to change that. I don't know if it work with other desktops like KDE. 

A simple solution to a minor issue that I spend a couple days tracking down. ](*,)

---

### Post by frodon on 2007-01-10
I suggest you to just bind your Right alt key to your Left alt key.

Run "xev" (type xev in a terminal to launch it)  and press the key you want to remap here you right Alt key, you should see this kind of output in the terminal :
```
KeyRelease event, serial 26, synthetic NO, window 0x2e00001,
    root 0x3e, subw 0x0, time 1011248671, (245,-109), root:(249,344),
    state 0x90, **keycode 113** (keysym 0xfe03, ISO_Level3_Shift), same_screen YES,
    XLookupString gives 0 bytes:  ""
```Note the keycode of your right Alt key then use a xmodmap command to bind it to your left Alt key :
```
xmodmap -e "**keycode 113** = Alt_L"
```Replace keycode 113 by the keycode of your right Alt key.

Once it works, if you want this to be set at startup put this line in a script and add the script to the startup session scripts.

---

### Post by tweedledee on 2007-01-10
> **Patrick K said:**
> In stock form Ubuntu (Gnome) comes with the right side Alt ket bound to AltGr which, so I have read, is for typing special characters. Many of us have no need for this and would like the right key to work the same as the left Alt key. 

To fix this go to  [System-Preferences] and open the Keyboard applet. Click on the Layout Options tab and "Alt/Win key behavior" then check "Alt and Meta are on the Alt key (Default)". Why it says default, I don't know. After that the right Alt key works the same as the left one.

This doesn't change the key's behavior in the Console, though. I don't know how to change that. I don't know if it work with other desktops like KDE. 

A simple solution to a minor issue that I spend a couple days tracking down. ](*,)

Perhaps even easier: the real issue is that the right Alt is bound to the "3rd level choosers" for the keyboard (which I can't even view in Edgy because the display is broken...).  Anyway, go to System -> Preferences -> Keyboard -> Layout Options, and select 3rd Level Choosers.  Chances are the Right Alt is the key associated with this; just change it to soemthing else (I use 2nd Win key, since I don't need 3rd level chooser and don't actually have this button on my keyboard, so it just effectively disables it).

Caveat is that some key bindings actually specificy the right or left Alt key explicitly; in that case you need to use the previous poster's idea of just binding the right to the left, since most keybindings choose the left.

---

### Post by Tomone on 2008-07-14
It seems like in the "Third level choosers" section, the right alt key will always be set as a third level chooser unless the "Right alt key never chooses 3rd level" option is checked. I'm not sure if that option is always there (I don't remember having to check that box before) but at least that was what finally worked for me.

---

