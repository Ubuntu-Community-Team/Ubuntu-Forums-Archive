---
title: "Purple login screen, unable to change."
date: 2013-09-12
forum: General Help
---

### Post by Coder88 on 2013-09-12
Wiped Windows 7 off my laptop, installed Ubuntu 13.04 i386, gnome desktop. Added Ubuntu Tweak and set it to use same picture as my wallpaper for the background image for the login screen (did this on my desktop ubuntu and and worked fine). But when I logout (even did a reboot) all i see is that ugly purple colored background for the login screen. (And who the heck is making such a decision to use purple for such colors for an operating system for millions, wtf?). What am i doing wrong, why isn't the Ubuntu Tweak change working for the login screen background? Is there another config file somewhere I could manually configure? Could it be the image needs to be resized to be the same size as the screen resolution?

EDIT: I found the files to manually alter if need be, i just thought there might be a simple tweak tool (beyond Ubuntu Tweak).  The whole ugly purple scheme-- its images and scripts that control the background colors for all things ugly purple, seem be located in
 /lib/plymouth/
Found a script there that creates the ugly purple gradients on splash and also the login screen. Can't wait to change the purple to just black.

---

### Post by CatKiller on 2013-09-13
It's potentially a permissions issue; if the lightdm user can't read the location of your wallpaper, it can't display it. Just a thought.

---

### Post by Coder88 on 2013-09-13
> **CatKiller said:**
> It's potentially a permissions issue; if the lightdm user can't read the location of your wallpaper, it can't display it. Just a thought.

I thought that too, checked so anybody could read the image.
I will keep working on this.

---

