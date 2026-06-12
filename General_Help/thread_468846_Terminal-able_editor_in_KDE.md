---
title: "Terminal-able editor in KDE"
date: 2007-06-09
forum: General Help
---

### Post by Cilionelle on 2007-06-09
Anyone help me with this?  I'm looking to edit my xorg.conf but can't find an editor that works.

---

### Post by ajgreeny on 2007-06-09
You can use kate or any of the text editors, but you must do it as root:-
kdesu kate /etc/X11/xorg.conf
will open kate as root and then you will be able to change it to your heart's content.

Keep a backup copy first, however, as the you can restore if things go wrong.
sudo cp /etc/X11/xorg.conf /etc/X11/xorg.confbackup.

If you want to use a terminal application, try nano:-
sudo nano /etc/X11/xorg.conf

---

### Post by Cilionelle on 2007-06-10
Thanks!  I'll try that out!

---

### Post by ThinkBuntu on 2007-06-10
If, for some reason, Kate is too slow for your purpose, don't forget KWrite and even KEdit.

---

