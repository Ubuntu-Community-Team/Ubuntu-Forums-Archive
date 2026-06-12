---
title: "Lost use of my delete key in X - please assist"
date: 2006-11-05
forum: General Help
---

### Post by russofris on 2006-11-05
Good evening,

I was creating a couple of keyboard shortcuts in gnome:

System -->  Preferences --> Keyboard Shortcuts.

During the process, I created a bad entry, so I clicked on it and hit delete.  Unfortunately, I must have mistakenly dbl clicked, as "Delete" was now bound to the "pause" function for my music player.  I highlighted the entry and hit backspace, successfully removing the binding to my delete key.

Now the bad.  My "Delete" key no longer works.  I assume that there is a file somewhere in which my Delete key has been reserved as a Gnome keyboard Shortcut, but I am unable to find it.  It does not appear in the keyboard-shortcuts GUI.

I have referred to to the "Help" under "Keyboard Shortcuts" but it does not go into the level of detail necessary for tracking the problem down.  Does anyone know how I can regain the use of my delete key?

Thank you for your time,
Frank Russo

---

### Post by russofris on 2006-11-05
This issue has been resolved using the following steps.

1:  Reset the keyboard shortcuts to their default state

frusso@frusso-desktop:~$ gconftool-2 -s -t string /desktop/gnome/interface/gtk_key_theme "default"

2:  Reboot


Please note that a simple reboot after removing the key binding was not successful.  I had to forcefully revert the shortcuts.

Thank you for your time,
Frank Russo

---

