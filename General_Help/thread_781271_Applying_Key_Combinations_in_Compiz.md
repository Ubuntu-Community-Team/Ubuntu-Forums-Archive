---
title: "Applying Key Combinations in Compiz"
date: 2008-05-04
forum: General Help
---

### Post by kevinjones on 2008-05-04
I've installed Hardy (although I think this was also an issue in previous releases) and I'm trying to get my windows key working with various combinations.

In Keyboard Preferences I have "Super is mapped to Win Keys"

In Keyboard Shortcuts I have 
Mod4+E mapped to "Home Folder", 
Mod4+R mapped to "show the panel run application dialog"
Mod4+F" mapped to search
Ctrl-Escape mapped to show the panel menu

I have Compiz enable and in compiz I have
<Super><Shift>E mapped to Expo (not Super+E which is the default)
<Super>r mapped to Run
<Super>m mapped to minimize to Show Desktop

Some of these work, some don't

In particular the Compiz settings work, but things like Super|Mod4+e to show the home window Super|Mod4+F for search and Ctrl+Esc do not work.

I'm sure I had Ctrl+Esc working before I restarted the window manager but it's stopped now. 

Any ideas on how to fix this? I think it's a clash between compiz and the gnome window manager, compiz is grabbing the keys first and gnome isn't seeing them.

Any help appreciated.

Kevin

---

### Post by kevinjones on 2008-05-04
To partly answer this myself.

I did manage to get Super+e and Super+L working.

To do this I had to disable all references to these keys in the gnome keyboard preferences and edit them in the compiz settings. 

In compiz I added to commands: nautilus and gnome-screensaver-command --lock and bound these to two keys <Super>e and <Super>l

Not ver satisfactory but it works.

See

[https://bugs.launchpad.net/gnome-control-center/+bug/12153](https://bugs.launchpad.net/gnome-control-center/+bug/12153)

for more details of this.

However I still don't have Ctrl+Esc working!

Kevin

---

