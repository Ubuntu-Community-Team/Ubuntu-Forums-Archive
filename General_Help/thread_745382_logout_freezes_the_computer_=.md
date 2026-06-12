---
title: "logout freezes the computer =/"
date: 2008-04-04
forum: General Help
---

### Post by icd* on 2008-04-04
We (my dad) upgraded our computer from feisty to Gusty, and since then if i click on the logout button, or choose logout in the menu the desktop freezes.

when i say freezes, the mouse moves, music continues to play, and the numlock lights still work on the keyboard, but nothing happens if i click or type anything.


The only current way i have of exiting the session is "Control-Alt-Backspace" which is a pain in the neck, as afaik, the session isnt saved. it used to work fine on feisty, could it be something to do with my theme, or have i messed something up in gconf editor?

help? :P

---

### Post by prshah on 2008-04-04
> **icd* said:**
> We (my dad) upgraded our computer from feisty to Gusty, and since then if i click on the logout button, or choose logout in the menu the desktop freezes.
help? :P

You have probably removed the gnome-power-manager from your sessions. Easy to fix. Press Alt+F2 and type "gnome-power-manager" in the command box and click Run / press Enter. Then try to logout. If it works, you can make it permanent as below:

Open sessions (System->Preferences->Sessions) and look for an entry "Gnome Power Manager". If it is there, it should be ticked. If it is not there, just add it by clicking the "+Add" button and entering "gnome-power-manager" in the space for "command". You can (optionally) fill in a description and name if you want, then OK.

---

### Post by icd* on 2008-04-04
haha! thanks very much, brownie points to you =p



cheers =]

---

### Post by ebash on 2008-05-18
This is a real lifesaver.

Thanks.

---

