---
title: "Finding icons for document types"
date: 2008-02-15
forum: General Help
---

### Post by Aholiab on 2008-02-15
How can I assign appropriate icons to my documents? In particular, I'm looking for an icon for KeePass. I know where the executable is located, I think, but when I point to this from the menu stuff to change the document icon, it doesn't see an icon there at all.

In the meanwhile, I have gathered icons for a few programs like this, but it seems that I should be able to get the icon from the program. Maybe I'm too Windows-centric still?

---

### Post by airtonix on 2008-02-15
thisis becuase, unlike windows or mac.....linux doesnt keep the program realted icons with the program executable files.

here is a diagram explaining the layout of a general filesystem in linux : 

> [http://img81.imageshack.us/my.php?image=linuxfilestructure6xk.jpg](http://img81.imageshack.us/my.php?image=linuxfilestructure6xk.jpg)there are two places for your icons to go.

1 - the system wide, avail to all who have accounts on the computer are at : > /usr/share/pixmaps

2- your personal collection at : > /home/username/.icons

you will also notice they are then group per theme, or not(mostly for neatness and packaging purposes). but you will laso notice that gnome requires a specific naming convention for each icon. im not sure waht this is yet, something youll have to look for.

---

