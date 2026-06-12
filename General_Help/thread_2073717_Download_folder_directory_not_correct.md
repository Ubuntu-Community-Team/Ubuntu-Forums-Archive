---
title: "Download folder directory not correct"
date: 2012-10-20
forum: General Help
---

### Post by Myki on 2012-10-20
I'm not exactly sure how to explain this, so please keep that in mind. It's annoying, to say the least.

I accidentally moved my downloads folder to my desktop. When I move it to my home folder, where with my documents, pictures, etc, are. I get this when clicking on the Downloads link in the sidebar of my file browser (which is stock)....

> Could not find "/home/mike/Desktop/Downloads".If I drag it back to the desktop, it's perfectly fine. Problem is I don't want the folder on my desktop. I want it the way it *was*.

So, how do I get it back how it was? I have searched EVERYWHERE via Google, couldn't come up with a solution. 

I'd appreciate any help.

---

### Post by drmrgd on 2012-10-20
I believe that sidebar link it easily editable.  As I don't use Nautilus since I'm on Kubuntu, I'm not exactly sure how differently it works.  However, I believe you can just right click on the link in your file browser and edit the path to point to where ever you move your Downloads directory.  This works in Dolphin, the default KDE file manager.  See if it's the same in Nautilus.

---

### Post by raja.genupula on 2012-10-20
how about this ??
 
```
mkdir /home/mike/Desktop/Downloads
```

---

### Post by mc4man on 2012-10-20
Open this file & edit back to orig. location as in screen
```
gedit .config/user-dirs.dirs
```

---

### Post by Myki on 2012-10-20
> **mc4man said:**
> Open this file & edit back to orig. location as in screen
```
gedit .config/user-dirs.dirs
```

My hero! ^_^

Thank you so much, that worked perfectly.

---

