---
title: "Virtualbox doesnt send 'Ctrl' to Windows guest"
date: 2007-05-11
forum: General Help
---

### Post by vav on 2007-05-11
I cant use Ctrl+C and such shortcuts in my Windows guest... that's really annoying! How do I get Virtualbox to pass Ctrl key presses to windows? This is both the left and right control keys.

---

### Post by vav on 2007-05-27
:bump:
Any help please?

---

### Post by robrmd9 on 2007-05-27
It is possible that VirtualBox doesn't let 'Control' pass through to the Guest OS because it is set as the Host Key (I believe 'Control_R' is the default), so try going to File->Global Settings->Input and then setting another key as the Host Key.

---

### Post by vav on 2007-05-30
I've changed my host key to 'menu' on my keyboard. So it shouldnt be that anymore :(

---

### Post by mrf76 on 2007-09-05
Solved problem with uncheck default option in Gnome:
System -> Preferences -> Mouse -> Pointers -> Locate Pointer -> Highlight the pointer when you press Ctrl. Hope it helps.

---

### Post by felipelavinz on 2007-10-21
where did the "highlight mouse pointer" option went on gutsy/gnome 2.20?

---

### Post by kblood on 2007-10-26
Same problem here on Gutsy: I had that option enabled on Feisty, and now I can't disable it!!! Extremely annoying!

Someone help!!

---

### Post by kblood on 2007-10-26
Found it!

Use the Configuration Editor, and go to:

/desktop/gnome/peripherals/mouse/locate_pointer

and disable it, of course.

Effect is immediate, no need to reboot! :)

---

