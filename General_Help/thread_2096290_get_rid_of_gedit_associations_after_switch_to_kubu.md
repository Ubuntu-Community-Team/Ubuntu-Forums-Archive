---
title: "get rid of gedit associations after switch to kubuntu?"
date: 2012-12-19
forum: General Help
---

### Post by poikiloid on 2012-12-19
I did a fresh install of Kubuntu 12.10, after having used regular Ubuntu. I keep /home in separate partition.

After switching, I still find gedit listed in the K-menu launcher, and many types of files are still associated with gedit, even though gedit is not installed... Clicking gedit in launcher gives error, obviously.

How to fix?

Can I remove gedit association from all those filetypes at once somehow, or must I do each type individually?

---

### Post by oldos2er on 2012-12-19
See [http://ubuntuforums.org/showthread.php?p=8365164](http://ubuntuforums.org/showthread.php?p=8365164)

---

### Post by poikiloid on 2012-12-19
thanks. found it in ~/.local/share/applications. made a zip backup in case i ever go back to reg ubuntu, then deleted it. ran kbuildsycoca4. restart. all good.

---

