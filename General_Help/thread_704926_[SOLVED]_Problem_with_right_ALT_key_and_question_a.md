---
title: "[SOLVED] Problem with right ALT key and question about touchpad"
date: 2008-02-22
forum: General Help
---

### Post by crosswalker21 on 2008-02-22
I have 3 questions that I'm hoping someone can answer.

1 - The right alt key on my compaq presario 2200 laptop doesn't appear to work.  I know there's most likely a conf file somewhere that I can edit to fix that.  Does anyone know where I might find that, and, if so, what I should change?

2 - My laptop has a synaptic touchpad, which works well under Ubuntu (gutsy) except for a couple things.  In windows xp, I could double tap to "lock" a click (for dragging things around even after lifting my finger) I can't seem to find out how to do that in Ubuntu.  Am I missing something?

3 - Is there any way to configure the palm-check feature of my touchpad?  The way this laptop is set up, the sides of my thumbs tend to tap the touchpad inadvertently, which results in a whole bunch of unwanted clicks.

Thanks for any help!

---

### Post by soldats on 2008-02-22
hrmm you could always open a terminal and type "xev" and it should bring up a box in whick you can put your mouse in and type each alt key and see if it registers each one like Alt_R and Alt_L. maybe one of the keys is messed up. if in fact they do work maybe some apps your using have preconfigured it to only use one or the other alt key. 
im almost positive there is a way to set the sensitivity of the touchpad but im not a laptop user but i recall hearing about a way to do it. maybe someone else knows.

---

### Post by crosswalker21 on 2008-02-22
Tried it!
Here's the output if it helps anyone.

Left Alt key Press/Release
```
KeyPress event, serial 30, synthetic NO, window 0x5c00001,
    root 0x4d, subw 0x5c00002, time 1143368108, (32,26), root:(688,74),
    state 0x10, keycode 64 (keysym 0xffe9, Alt_L), same_screen YES,
    XLookupString gives 0 bytes: 
    XmbLookupString gives 0 bytes: 
    XFilterEvent returns: False

KeyRelease event, serial 30, synthetic NO, window 0x5c00001,
    root 0x4d, subw 0x5c00002, time 1143368393, (32,26), root:(688,74),
    state 0x18, keycode 64 (keysym 0xfe0a, ISO_Prev_Group), same_screen YES,
    XLookupString gives 0 bytes: 
    XFilterEvent returns: False
```

Right Alt key Press/Release
```

KeyPress event, serial 30, synthetic NO, window 0x5c00001,
    root 0x4d, subw 0x5c00002, time 1143371966, (32,26), root:(688,74),
    state 0x10, keycode 113 (keysym 0xfe03, ISO_Level3_Shift), same_screen YES,
    XLookupString gives 0 bytes: 
    XmbLookupString gives 0 bytes: 
    XFilterEvent returns: False

KeyRelease event, serial 30, synthetic NO, window 0x5c00001,
    root 0x4d, subw 0x5c00002, time 1143372136, (32,26), root:(688,74),
    state 0x90, keycode 113 (keysym 0x0, NoSymbol), same_screen YES,
    XLookupString gives 0 bytes: 
    XFilterEvent returns: False

```

---

### Post by Ctrl-Z on 2008-02-26
> **crosswalker21 said:**
> Tried it!
Here's the output if it helps anyone.

Left Alt key Press/Release
...
Right Alt key Press/Release
...


Had the same output from xev. This line at the end of ~/.bashrc seems to be helping

```
xmodmap -e "keycode 113 = Alt_L ISO_Prev_Group ISO_Prev_Group NoSymbol ISO_Prev_Group"

```

---

### Post by crosswalker21 on 2008-02-29
hmm. . .still nothing.  Guess I'll just have to dig around a bit more.  Thanks for trying to help though!

---

### Post by chewearn on 2008-02-29
About the right ALT key, see if this works for you.

Top Menu > System > Preferences > Keyboard > Layout Option tab

Somewhere in the might be the checkbox that will fix the problem; I can't remember which one, since I only need to investigate this once in the beginning.

---

### Post by domino1241 on 2008-03-03
It's "Alt and Meta are on the Alt keys."

[http://blog.andrewbeacock.com/2007/06/getting-right-alt-key-alt-gr-to-work-in.html](http://blog.andrewbeacock.com/2007/06/getting-right-alt-key-alt-gr-to-work-in.html)

---

### Post by crosswalker21 on 2008-03-06
That was way too easy.  Especially since I looked at that checkbox a dozen times and figured it wouldn't do what I needed.  Thanks everybody!!!

---

