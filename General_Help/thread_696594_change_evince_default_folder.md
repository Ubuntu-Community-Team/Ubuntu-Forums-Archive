---
title: "change evince default folder??"
date: 2008-02-14
forum: General Help
---

### Post by guano on 2008-02-14
Hello.
First, let me say that there is one thing that I found really annoying in Ubuntu 7.10, which is the creation of those default folders in your /home (Documents, Music, etc..). I really hate those. I use Linux for almos seven years now, and I have my own schema. So I just delete those folders after installation, but for some reason, Evince keeps looking for /home/guano/Documents, every time it is started by it self (that is, not by double-clicking in a pdf file).
So, is there a way I can change this "default"  folder? I looked in .gnome2/evince/evince-metadata.xml and also in gconf2. Nothing.

Does anyone how to change this?

thanks in advance

---

### Post by erginemr on 2008-02-14
The file to change is a config file in a hidden folder in your home folder:
```
gedit ~/.config/user-dirs.dirs
```
make the changes as you like, save and close. And then, run:
```
xdg-user-dirs-update
```
to reflect the changes.

---

### Post by guano on 2008-02-14
Many thanks!

---

### Post by erginemr on 2008-02-14
You are most welcome. FYI, by the way, you can mark a thread as solved by selecting it from under the "Thread Tools" drop-down menu on top of this page.

Have Fun!

---

