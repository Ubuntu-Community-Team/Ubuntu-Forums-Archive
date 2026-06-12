---
title: "Removing a Program"
date: 2019-10-06
forum: General Help
---

### Post by greenredbean on 2019-10-06
I installed lightshot, then used the provided uninstaller to try to remove the program. However, the icons for "Lightshot" and "Uninstall Lightshot" can still be found on the applications menu. When I try to open either of these applications, I get a message shown in this image ([https://imgur.com/gallery/M8sOLfp](https://imgur.com/gallery/M8sOLfp)). I am a complete beginner at this, so any help would be very much appreciated! Thanks.

---

### Post by Dennis N on 2019-10-06
Looks like it was running under Wine? I would look for a .desktop file, possibly in **~/.local/share/applications**, and delete it if present. That should remove the launcher after reboot.

---

### Post by CatKiller on 2019-10-06
Windows applications (and so also Windows applications installed through Wine) are generally terrible at cleaning up after themselves.

The launchers are simply text files (.desktop files in this case) that for a per-user installation will be in ~/.local/share/applications. You can just delete them if you don't want them any more.

---

### Post by Skaperen on 2019-10-06
> **CatKiller said:**
> Windows applications (and so also Windows applications installed through Wine) are generally terrible at cleaning up after themselves.

they don't have world wide community to answer to.

---

### Post by greenredbean on 2019-10-06
Thanks so much for the quick help! My problem was solved by deleting the file from ~/.local/share/applications/wine . :D

---

