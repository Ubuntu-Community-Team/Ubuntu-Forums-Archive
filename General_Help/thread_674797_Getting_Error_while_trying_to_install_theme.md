---
title: "Getting Error while trying to install theme"
date: 2008-01-22
forum: General Help
---

### Post by SoberWarlock on 2008-01-22
So i'm trying to install this theme, but I can't so how can I do this? Here is what i'm getting

[IMG]http://i63.photobucket.com/albums/h144/Jorale_mendoza4/Errors/Screenshot.png[/IMG]

---

### Post by aidanr on 2008-01-22
You can copy it to ~/.themes (Ctrl+H in your home folder to show hidden files and folders). 
You only need to copy it to /usr/share/themes if it needs to be used by multiple users, if thats the case then open a terminal and type ```
gksudo nautilus
``` to run the filebrowser as root and copy it from there.

---

### Post by SoberWarlock on 2008-01-22
> **aidanr said:**
> You can copy it to ~/.themes (Ctrl+H in your home folder to show hidden files and folders). 
You only need to copy it to /usr/share/themes if it needs to be used by multiple users, if thats the case then open a terminal and type ```
gksudo nautilus
``` to run the filebrowser as root and copy it from there.

Thank you man I got it to work now I know what to do for next time. 

Now I have another problem. I can't get these files to work: .cgwdtheme or .cgwd I get some kind of archive error.

---

### Post by aidanr on 2008-01-22
Cgwd is obsolete, it was replaced by Emerald. So either install Emerald and use [Emerald themes]("http://gnome-look.org/?xcontentmode=103"), or stick with gtk-window-decorator and use [Metacity themes]("http://gnome-look.org/index.php?xcontentmode=101").

---

### Post by SoberWarlock on 2008-01-22
> **aidanr said:**
> Cgwd is obsolete, it was replaced by Emerald. So either install Emerald and use [Emerald themes]("http://gnome-look.org/?xcontentmode=103"), or stick with gtk-window-decorator and use [Metacity themes]("http://gnome-look.org/index.php?xcontentmode=101").

Well Aidanr you have been such a great help :) I have everything working now. THANKS A LOT man! :)

---

