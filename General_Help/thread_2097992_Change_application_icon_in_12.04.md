---
title: "Change application icon in 12.04"
date: 2012-12-25
forum: General Help
---

### Post by Panawe on 2012-12-25
How do I change the application icon is 12.04? This used to be easy but I've forgotten how?
I've installed Shredder from a .tar file and am stuck with generic icon!
TIA

---

### Post by vasa1 on 2012-12-25
Would editing the respective .desktop file (/usr/share/applications) help? There's a line with "Icon=whatever" and you can replace whatever with the path of the icon you desire.
You could also copy over the .desktop file to ~/.local/share/applications and fiddle with it there, safe in the knowledge that the system one isn't ruined ;)

---

### Post by Panawe on 2012-12-25
Okay, done that. Thanks :)

---

