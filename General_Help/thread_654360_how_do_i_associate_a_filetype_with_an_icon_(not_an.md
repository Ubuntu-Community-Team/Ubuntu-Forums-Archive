---
title: "how do i associate a filetype with an icon (not an app)"
date: 2007-12-31
forum: General Help
---

### Post by bpont on 2007-12-31
i know how to associate a filetype with an application (right click, properties, open with, etc.), but i need to learn how to associate an icon with a particular filetype...i searched the forum, but no luck...can anyone help?

in particular, i want the filetype '*.xspf' to display an audacious playlist icon.

thx

---

### Post by dlegend on 2007-12-31
See this thread: [http://ubuntuforums.org/showthread.php?t=302549](http://ubuntuforums.org/showthread.php?t=302549) (titled **HOWTO: Change icon for specific file types in Gnome**)

---

### Post by bpont on 2007-12-31
here's how i got it to work:

```
sudo cp /usr/share/audacious/images/playlist.png /usr/share/icons/gnome/64x64/mimetypes/gnome-mime-application-xspf+xml.png
```

i had to create the 64x64/mimetypes subdirectories, because they didn't exist and the icon i wanted to use was 64x64.

after i ran that command, i just logged out/in and the xspf files had the desired icon.

---

