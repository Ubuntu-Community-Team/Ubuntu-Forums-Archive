---
title: "How do I copy the current path/filename in File Manager?"
date: 2019-11-16
forum: General Help
---

### Post by yaminb on 2019-11-16
Question is as in the title.
How do I quickly copy the current path in File Manager?

I resort to some pretty silly ways.
Like clicking properties on a directory/file and then I can copy the 'parent folder' field.

In windows at the top of windows explorer, the path is selectable as text. I'm sure there must be an easier way. 
I keep reading about context aware copying and pasting. 
Maybe I'm just doing it wrong. But I just want to copy the path to say gedit to save a note or something.

---

### Post by CatKiller on 2019-11-16
In most file browsers hitting Ctrl-L will bring up the location bar.

---

### Post by him610 on 2019-11-16
My File Manager (Thunar) has a space in the upper window that shows the folder/directory location. All that needs to be done is highlight the folder then Ctrl-C to copy. Refer to attachment.

---

### Post by yaminb on 2019-11-16
> **CatKiller said:**
> In most file browsers hitting Ctrl-L will bring up the location bar.

That did it. Ctrl-L. 
Just for the record, I was talking of the standard ubuntu gnome file-manager (nautilis)

I found this open in dconf-editor that makes it a permanent address bar that you can copy and paste.
I'm not sure if it's better for usability, but ill play with it.

org.gnome.nautilus.preferences always-use-location-entry true

---

### Post by vanadium on 2019-11-19
Also in nautilus, you can press Ctrl+L to display and focus the path bar. thus, a Ctrl+L Ctrl+C will copy the pathname of the current folder. In the version of nautilus that ships with 18.04, the clipboard contains the pathname of the selected file(s) if you hit Ctrl+C. That is broken in more recent nautilus versions (in particular nautilus 3.34 that comes with Ubuntu 19.10).

---

