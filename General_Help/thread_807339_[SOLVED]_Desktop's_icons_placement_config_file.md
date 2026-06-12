---
title: "[SOLVED] Desktop's icons placement config file"
date: 2008-05-25
forum: General Help
---

### Post by priegog on 2008-05-25
Hi. To make a VERY long story short, I did a straight transfer of my /home folder into a new computer with a smaller screen. The problem is some of the icons I had placed in the far right of my bigger screen and don't show up in the smaller one. For the folders that were there, I could solve it by opening a nautilus windows, going to the desktop and dragging the icons to their new position on the real desktop. But one of the things I dragged was the icon of my flash drive when it is connected and automounted, and THAT I cannot reposition in such a way. I'm therefore looking for the specific file (or portion in some other config file) that stores the coordinates for icons in the Desktop. Thanks.

---

### Post by Brucevdk on 2008-05-27
Check out the file:
```
~/.nautilus/metafiles/file:%2F%2F%2Fhome%2F**$USER**%2FDesktop.xml
```

Where $USER points to the current logged in user.

---

### Post by priegog on 2008-05-27
Ah.... thanks a bunch!

---

### Post by Socca on 2008-09-02
> **Brucevdk said:**
> Check out the file:
```
~/.nautilus/metafiles/file:%2F%2F%2Fhome%2F**$USER**%2FDesktop.xml
```

Where $USER points to the current logged in user.


How do i access that?

---

### Post by durand on 2009-06-27
Go to ~/.nautilus/metafiles/ with the file manager and find the file:%2F%2F%2Fhome%2F$USER%2FDesktop.xml file where $USER points to the current logged in user. ~ is a shortcut for your home folder.

---

