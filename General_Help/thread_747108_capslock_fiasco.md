---
title: "capslock fiasco"
date: 2008-04-06
forum: General Help
---

### Post by kosmos on 2008-04-06
I was typing a letter in gmail in a konqueror window when I hit some key sequence that turned on capslock. This is bizarre because I use xmodmap to turn capslock into control_L. I have no idea what could have started capslock mode.

So, now that I'm in capslock mode, without any capslock key, because I F**KING HATE CAPSLOCK, I cannot do anything at all. All my sawfish windowmanager functionality does not recognize hotkeys or mouse buttons with the shift mode on, so I cannot switch windows or desktops, or get a terminal window or anything.

I logged in remotely and killed the X server to get back to the console window and it was still in capslock mode. Unfortunately, I do not have a "SHUTDOWN" command on my system, only the cheaper "shutdown" version. The only thing I could do was log in remotely and reboot.

So, my questions are:
- How can capslock get turned on when I do not have a capslock key? 
- How can I turn off capslock mode if I do not have a capslock key?
- How can I prevent this from happening in the future?

Thankyou.

---

### Post by TeoBigusGeekus on 2008-04-06
Have you tried to go to System -> Preferences -> Keyboard Shortcuts or just Keyboard to see if you can make out something?

---

### Post by kosmos on 2008-04-06
> **TeoBigusGeekus said:**
> Have you tried to go to System -> Preferences -> Keyboard Shortcuts or just Keyboard to see if you can make out something?

I do not have that on my system as I do not run Gnome or KDE. I just run the bare sawfish windowmanager with my own custom menus and hotkeys.

---

### Post by bcl1713 on 2008-04-06
Sounds to me like you may have gotten stickey keys turned on by accident it has happened to me before and is under keyboard accessability in 7.10.  A simple double tap of the shift key may have reverted you back to "caps lock" off.
EDIT or not.. your statement about not having gnome or kde came up as I was posting.

---

### Post by kosmos on 2008-04-06
> **bcl1713 said:**
> Sounds to me like you may have gotten stickey keys turned on by accident it has happened to me before and is under keyboard accessability in 7.10.  A simple double tap of the shift key may have reverted you back to "caps lock" off.
EDIT or not.. your statement about not having gnome or kde came up as I was posting.

I did try tapping the shift key, once, twice, many times, but it didn't turn off capslock.

---

### Post by kosmos on 2008-04-06
Maybe I should refine what I'm looking for:

1) Is there a way to disable capslock mode (not just remap the key, as I do with xmodmap?) I want it gone, as in never to return even if I don't remap my capslock.
2) If not, is there a command line I can run that will turn off capslock mode, should it ever get enabled again? I can map that to a shifted command via sawfish and then I should be able to get out of the situation should it arise again.
3) When is the next chapter meeting of the CAPSLOCK IS EVIL ASSOCIATION? Apparently I'm late in my dues.

---

