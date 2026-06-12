---
title: "[SOLVED] Missing gdm file"
date: 2007-08-11
forum: General Help
---

### Post by Goombie on 2007-08-11
I installed KDE desktop yesterday in Ubuntu, and I mistakenly set the default display manager to kdm, instead of keeping it at gdm like I wanted. I've found the file to edit fto set the default display manager, but I don't know the path for the gnome display manager. I looked in /usr/bin, where kdm is,  but I didn't find it there. I'm not sure where else to look. I have gdm installed on my system, but it's not starting up. Any ideas? :confused:

---

### Post by forestpixie on 2007-08-11
You should be able to change the default before you login - bottom left - sessions I think , or maybe options - change to gnome there.

---

### Post by apetresc on 2007-08-11
> **forestpixie said:**
> You should be able to change the default before you login - bottom left - sessions I think , or maybe options - change to gnome there.

No, that's not what he's asking -- he wants to actually change which manager to use, not which desktop the manager boots to. The distinction is between kdm/gdm not kde/gnome.

Goombie, you want to do ```
sudo dpkg-reconfigure kdm
```

---

### Post by forestpixie on 2007-08-11
My bad - :) and I learnt a new thing :D

Wonder if he/she will read both of our sigs!

---

### Post by Goombie on 2007-08-11
> **AdrianP said:**
> No, that's not what he's asking -- he wants to actually change which manager to use, not which desktop the manager boots to. The distinction is between kdm/gdm not kde/gnome.

Goombie, you want to do ```
sudo dpkg-reconfigure kdm
```

Actually, that command didn't work for changing the display manager for me. However, it did point me in the right direction. I did
```
sudo dpkg-reconfigure gdm
```
And selected gdm as my default display manager. I rebooted to test the settings, and it worked fine! Thanks for your help, both of you. :) And yes, I will mark this thread as solved.:popcorn:

---

