---
title: "&quot;Reseting&quot; the desktop on upgrade"
date: 2008-05-14
forum: General Help
---

### Post by eks on 2008-05-14
Hellos!

I've posted about this some weeks ago on Installation and Upgrades forum but got no reply. I want to make the upgrade to Hardy but "reset" everything "desktop related". I will be using the upgrade function just for testing then later installing Hardy from scratch from the cd.

BUT!

I would like to **"reset" my desktop**. That is, I would like to reset all the configuration from Compiz/effects, themes, icons, backgrounds, fonts, etc. From what I understand, I should **just delete/rename some /home/.gnome directories** from my /home (which is on another partition).

My question is: which ones?

All /home/.gnome*? Any thing else? /home/.metacity maybe? What is /home/.gconf and .gconfd?

**Or in short, where can I find everything desktop related in Ubuntu?**

Thanks!
eks

---

### Post by ayoli on 2008-05-14
```
~/.gnome*
~/.config
~/.themes
~/.icons
~/.fonts
~/.gconf*
```
are the directories that come to my mind regarding your needs

hope that helps.

cheers.

---

### Post by eks on 2008-05-15
Yes, it does!


Merci! :D
eks

---

