---
title: "Keyboard language change and keymaps"
date: 2017-03-07
forum: General Help
---

### Post by vegarab on 2017-03-07
Hi.
I am using a Mac-keyboard, with the English (UK, Intl.) layout, and have that set as my Text Entry in Ubuntu. I have a Xmodmap script that runs on boot to change swap CTRL and CMD on my keyboard (CMD is treated as Super by default). This gives me Mac-like shortcuts. In order to have my script run, I had to disable the gnome daemon settings for the keyboard, since it kept changing my ctrl-cmd swap. 
I disabled it using this:

```
gsettings set org.gnome.settings-daemon.plugins.keyboard active false

```

Now I cannot change the Text Entry (language) on my keyboard. I am Norwegian and occasionally need Norwegian letters, which are only on the norwegian keyboard. 
I need a way to actually change the Text Entry language now that I have the deamon plugin for the keyboard disabled. The way I deal with this in OS X, is that with the English keyboard, I can press ALT-{button} to get my 3 Norwegian letters. 
Is there a way to set up that as a keybind/macro?

Also, whenever I want to make " or ', I have to hit the button/shift-hit the button AND press space from them to show. Is there a way to have them appear right away, without me having to hit space? That is, from my use of Windows and OS X, the normal behaviour. (Its the button above / and left-shift).

Thank you.

---

