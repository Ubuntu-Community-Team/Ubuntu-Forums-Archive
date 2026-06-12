---
title: "[SOLVED] open evolution preferences crash"
date: 2008-06-13
forum: General Help
---

### Post by KaliVoid on 2008-06-13
Hi

When i open evolution preferences (and plugins) it crashes every time.

i found this bug reports "[icons]("https://bugs.launchpad.net/ubuntu/+source/librsvg/+bug/133692")" & "[aspell]("http://bugzilla.gnome.org/show_bug.cgi?id=232230")" i remove all downloaded icon themes and aspell but the problem continues.

when i open evolution in terminal i can open preferences and an error shows in the terminal "(evolution:8475): evolution-mail-WARNING **: Cannot activate OAFIID:GNOME_Spell_Dictionary:0.3"

also i cant find evolution error logs ,where are they ?

---

### Post by KaliVoid on 2008-06-15
after doing apt-get autoremove (without any context to this problem) i saw it removed some spelling files
so i check evolution preferences and it didnt crash but there wasn't any spelling dictionary.
searching the forum i found [this]("http://ubuntuforums.org/showthread.php?t=699862") & [that]("http://ubuntuforums.org/showthread.php?t=52") so i reinstall gnome-spell and the language file and now everything back to normal :)

---

