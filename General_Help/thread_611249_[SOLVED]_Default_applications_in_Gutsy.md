---
title: "[SOLVED] Default applications in Gutsy"
date: 2007-11-12
forum: General Help
---

### Post by awsutter on 2007-11-12
I've experienced a strange issue with my current install of Ubuntu 7.10 where the default application to handle certain file types don't seem to be defined, or can be defined manually but still doesn't seem to be handled correctly. I built a new box at the same time Gutsy was released, so I don't have my old Feisty machine around as a reference, but I'm sure that these things used to work. None of this makes much sense.. am I missing something?

In my home folder, I've got .jpg files with no default app until I defined it. Once set, the default held and does open with Gnome Image Viewer, though the icon doesn't show as a thumbnail. Didn't that used to work? Application had to be set for .png files, and for some reason, about half of these show up as thumbnails, with no apparent reason. I've got .odt files that don't call OO and .html files that open in Text Editor. 

Any ideas? This is growing frustrating and I have half an idea to roll back to Feisty.

Thanks in advance..

---

### Post by rsambuca on 2007-11-12
You might try these first```
sudo update-mime-database
sudo update-desktop-database
```and if that doesn't work, try this```
sudo update-mime-database /usr/share/mime
sudo dpkg-reconfigure shared-mime-info
killall gnome-panel
killall nautilus
```

---

### Post by awsutter on 2007-11-12
Many thanks..  dpkg-reconfigure shared-mime-info did it for me. All is right again.

---

### Post by rsambuca on 2007-11-12
Wow!  We got lucky!  You may as well mark the thread as [solved] (in the thread tools).

---

