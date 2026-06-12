---
title: "How to Remap Remote Buttons"
date: 2008-02-23
forum: General Help
---

### Post by bt101 on 2008-02-23
Hi - I've spent an entire week trying to remap one remote button.  Any help would be greatly appreciated.

I purchased an RF USB keyboard and plugged it into my Gutsy box, and by some miracle, all of the multimedia keys worked out-of-the-box.  I fired up a few desktop multimedia apps and the play/prev/next/mute/volume keys worked, Hallelujah!

I then purchased a cheap MCE IR remote from ebay.  I would like to remap some of the keys to make them work like the ones on the RF keyboard.

I've been through every tutorial and have come up against a wall.

To get me started, could someone tell me how to remap one of these buttons.  Specifically, I know that one of the buttons produces CTRL+SHIFT+B.  I would like to remap this so that it will play the previous track.

If someone knows this, I think that would get me on-my-way.

I may be wrong, but I believe that you can completely ignore that fact that I'm using a remote control.  That is, you can think of the question as "How can CTRL+SHIFT+B on the KEYBOARD be remapped to play the previous track".

--------------------------------------

The rest of this is a bit of some background info (and a bit of a rant), so feel free to ignore.

What really has thrown-me, is that I would like to determine what my "working" keys are doing (so I can duplicate them) but I am having no luck at that.  Specifically, I want to see what the keys on the working RF keyboard are doing.  Most tutorials say that you should use XEV to see what keys are doing.  However, these keys on the RF keyboard produce nothing in XEV, yet they do work by some miracle.

I am able to get a response from those working multimedia keys when using lshal -m, however, that seemed to be a bit of a dead end.  I don't know what that tells me, or how it can help with any future key remappings

I am able to get a response from those working multimedia keys when using showkey -s or -k or -m.  I've looked at those numbers and have tried to fond out how they are related to xmodmao and can see no relation (another dead end).

So I was getting nowhere with the fundamentals, so I decided to leap ahead and try a program call keytouch.  I assumed that it would remap keys.  I started by using the keytouch editor.  I "added" a new key and hit the button on my remote that produces CTRL+SHIFT+B.  The keytouch editor saw that I hit the key (great).  I then went to save the file and it complained that the keys weren't associated with keycodes.  OK, I went back and selected the key, and then tried to select a keycode from the pull down.  It would not allow me to select a keycode (it just stayed blank).  So I ended up at another dead end.  I still don't know what keytouch does because I can't even get past the editor.

Thanks

---

### Post by SebMKd on 2008-05-26
Same problem here. Did you get anywhere in the meantime?

---

