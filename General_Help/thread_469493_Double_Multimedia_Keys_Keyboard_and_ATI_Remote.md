---
title: "Double Multimedia Keys: Keyboard and ATI Remote"
date: 2007-06-09
forum: General Help
---

### Post by Parksy on 2007-06-09
I have a keyboard with multimedia keys and a ATI remote.  I'd like to have both able to control my media player (rhythmbox).

Right now I use the "Keyboard Shortcuts" program to set which keys control Play/Pause, Previous Track and Next Track.  Unfortunately, this program only accepts one key.  If I set up the keyboard, the remote doesn't work, and vice versa.

One way I tried to fix this is setting keysyms on each of the keys.  Using xmodmap, I gave both "Next Track" keys the XF86AudioNext keysym.  Then I used the Keyboard Shortcuts program to set the "Skip to next track" shortcut to XF86AudioNext.  Unfortunately, still just one device works (whichever appears last in my xmodmap file).

Another idea is have is to change my keyboard keys to have the same keycodes as the remote.  However, I can't get this to work.  I get this error when running setkeycodes:
```

KDSETKEYCODE: No such device
failed to set scancode e6 to keycode 179

```
Not sure what this means. Is there another way to change keycodes or fix my problem?

---

