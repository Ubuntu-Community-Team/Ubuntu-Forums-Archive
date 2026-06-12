---
title: "Theme resets upon restart"
date: 2016-12-13
forum: General Help
---

### Post by pawn2 on 2016-12-13
[COLOR=#000000]I've installed the Numix theme (PPA) on a fresh Ubuntu 16.04 LTS installation.[/COLOR]
[COLOR=#000000]Everything looks great and works fine until I restart.[/COLOR]
[COLOR=#000000]Every time I restart it, the theme gets reset to the default Ubuntu theme. Once this reset happens, nothing happens when I change the theme/iconpack in Unity Tweak Tool/Gnome Tweak Tool etc.[/COLOR]
[COLOR=#000000]The weird thing is that logging out and in after starting up will apply the Numix theme and all the customizations again.[/COLOR]

[COLOR=#000000]Why is this reset happening? Is there any way to fix this?[/COLOR]

[COLOR=#000000]Also, the theme doesn't completely get reset upon restarting -- portions of the theme, like in address bar etc remains. But after logging out and in again, the Numix theme is perfectly intact.
(Accidentally posted a copy of this in a wrong section elsewhere, please remove that post.)[/COLOR]

---

### Post by vasa1 on 2016-12-13
> **pawn2 said:**
> ...
(Accidentally posted a copy of this in a wrong section elsewhere, please remove that post.)
Done! :)

FYI, there's a "report" button below and to the left of each post. You can click on that to
[LIST]
[*]report spam or advertising messages 
[*]request posts be moved or deleted,  
[*]report problematic (harassment, fighting, or rude) posts.
[/LIST]

---

### Post by pawn2 on 2016-12-17
Thank you, still having this problem.

---

### Post by pawn2 on 2016-12-18
Still looking for a solution to this.

---

### Post by Frogs Hair on 2016-12-18
Try installing the following if not already reset to the desired theme and logout or restart. You can set the theme from this application as well. Unity Tweak is basically a front-end for sconf-tools.  

```
sudo apt install dconf-tools
```

---

