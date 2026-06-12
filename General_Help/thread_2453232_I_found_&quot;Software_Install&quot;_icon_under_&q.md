---
title: "I found &quot;Software Install&quot; icon under &quot;Show Applications&quot;, what is it?"
date: 2020-11-05
forum: General Help
---

### Post by danwgrace on 2020-11-05
It doesn't do anything when I click the icon (a beige/brown rectangle with a line down the middle). Can I just remove this with "alacarte - Main Menu" or is there a package to remove? In general how do I see what command/executable/package is associated with an icon in "Show Applications".

I'm using Ubuntu 20.04.1 LTS.

Thanks.

---

### Post by deadflowr on 2020-11-05
Software Install is for installing off-line packages easily on the desktop.
But I don't think it's suppose to show.
It should only be available to use when you click double click on an installer file, like google-chrome's deb file.

In the old way it would be part of the gnome-software package and
the related file for it would be in the /usr/share/applications directory 
under the name gnome-software-local-file.desktop.

But 20.04 doesn't use gnome-software as it ships with the snap-store instead.
So I don't know where it's related file would be, nor how you could even edit it.
(or if it even exists)
But basically the file can be set to no show within it by adding the line
*NoDisplay=true* to it.

May be a bug.

---

