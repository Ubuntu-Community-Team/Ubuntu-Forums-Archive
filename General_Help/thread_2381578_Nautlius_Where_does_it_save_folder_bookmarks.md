---
title: "Nautlius: Where does it save folder bookmarks?"
date: 2018-01-02
forum: General Help
---

### Post by schnuckenack2 on 2018-01-02
Hello,

in which file does nautilus save its folder-bookmarks such as Home, Desktop, Pictures, Downloads, Music, etc.. and especially your custom created as shown below "Trash", "Network" and your filesystems.

Thank you very much

Yours

Schnuckenack

---

### Post by col48 on 2018-01-02
Trash is three folders at  /.local/share/Trash  (16.04)

In 12.04 there was a file /.gtk-bookmarks (human-readable with gedit) which listed the pertinent folders and could give them different names (eg non-English??) if desired. This does not include Trash.
But no such file exists on my 16.04 system, so things have changed.

By the way it isn't really Nautilus which is responsible, it is (was?) gnome, or whatever Desktop program is in use.

It would be helpful to include the name of the release you are using in your profile.

---

### Post by ajgreeny on 2018-01-02
You will find a file called bookmarks in ~/.config/gtk-3.0 which if you have not added any extra bookmarks will contain
```
file:///home/*user*/Documents
file:///home/*user*/Music
file:///home/*user*/Pictures
file:///home/*user*/Videos
file:///home/*user*/Downloads
```
Any extra folders you add manually will be added to that by the system.
My only use of nautilus is in 18.04 but I suspect this is what you will see in both 16.04 and 17.10 as well.

---

### Post by col48 on 2018-01-04
I confirm ajgreeny has identified the file for 16.04.  (I'm using nemo rather than Nautilus).

---

### Post by vasa1 on 2018-01-04
> **ajgreeny said:**
> ...
My only use of nautilus is in 18.04 but I suspect this is what you will see in both 16.04 and 17.10 as well.
Confirmed for Nautilus in 16.04.

---

