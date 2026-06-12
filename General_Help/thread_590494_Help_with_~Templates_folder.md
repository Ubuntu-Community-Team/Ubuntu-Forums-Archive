---
title: "Help with ~/Templates folder"
date: 2007-10-24
forum: General Help
---

### Post by tempest on 2007-10-24
I just installed Gutsy last week. After the install, I went ahead and cleaned out all the pre-installed empty dirs in my home dir including ~/Templates. Now I want to set up some template. In Feisty all I had to do was create a new ~/Templates folder and nautilus recognized it. Gutsy does not seem to want to use my newly created ~/Templates folder. Also when I go to Go -> Templates, nautilus just takes me to my home dir. Sounds like these are both related to me deleting some sort of link to the folder. Is there any way to create a new link? TIA.

---

### Post by grim4593 on 2007-10-24
Update the ~/.config/user-dirs.dirs
```
gedit ~/.config/user-dirs.dirs
```
Probably want the line that says:
XDG_TEMPLATES_DIR="$HOME/"
to say:
XDG_TEMPLATES_DIR="$HOME/Templates"

---

### Post by tempest on 2007-10-25
Thanks a bunch. This worked great.
--matt

---

### Post by Palmyra on 2008-03-01
Thanks...this helped me too!

---

