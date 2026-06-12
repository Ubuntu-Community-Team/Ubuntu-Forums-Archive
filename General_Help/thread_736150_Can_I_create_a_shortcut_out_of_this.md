---
title: "Can I create a shortcut out of this?"
date: 2008-03-26
forum: General Help
---

### Post by allanco on 2008-03-26
I have problems shutting Ubuntu down, it takes 50 seconds from hitting the quit button to then getting the various choices.
If I type sudo shutdown -h now, Ubuntu closes down in a snap.
Can I create a desktop shortcut from this?
Plus is there anything not happening when I close this way that could cause problems?
I am a Linux noobie!
Cheers

---

### Post by Sam Lars on 2008-03-26
Right click on the desktop and select "Create Launcher."  Fill in the info, with that as the command, and you should be good to go.

---

### Post by strabes on 2008-03-26
Ubuntu has a custom (and IMO, terrible) quit window. To revert to gnome's upstream version, run this command:```
gconftool-2 --set /apps/panel/global/upstream_session --type bool "1" && killall gnome-panel
``` Then choose System -> Shut Down. If you don't like it, just re-run the command with "1" replaced with "0". Hope this helps.

---

### Post by Sam Lars on 2008-03-26
Thanks strabes, that's interesting... any screenshots of the upstream window?

---

### Post by allanco on 2008-03-27
Many thanks for the help guys, I went with Strabes suggestion and it worked a treat.
Thanks again!:)

---

