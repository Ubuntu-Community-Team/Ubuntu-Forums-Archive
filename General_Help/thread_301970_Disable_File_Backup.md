---
title: "Disable File Backup"
date: 2006-11-17
forum: General Help
---

### Post by esaym on 2006-11-17
I like the file backup feature and it saved me a few times with xorg but I really don't like it when I edit a personal file in my home directory and it makes a copy of it.  Any way to disable this in  the home directory?](*,)

---

### Post by David_T on 2006-11-17
Which editor are you using?

---

### Post by esaym on 2006-11-18
Oh I forgot to mention.  I am using kubuntu so the editor is kate.  Let me check in the options...


Edit:

Ok I found the "save backup" option and it is set to "local files".  I am guessing there is no way to disable it in a selected directory?

---

### Post by CatKiller on 2006-11-18
> **esaym said:**
> Oh I forgot to mention.  I am using kubuntu so the editor is kate.  Let me check in the options...


Edit:

Ok I found the "save backup" option and it is set to "local files".  I am guessing there is no way to disable it in a selected directory?

If the mechanics on Kubuntu are the same as Ubuntu, then when you're writing to the kinds of directories you might want to write to, you are running **kate** as **you**. When you are writing to the kinds of directories that you might desperately need a backup, you're running **kate** as **root**. So if you turn the option off as you, is it still on when you run **kdesu kate**? In Gnome, **gedit** and **gksudo gedit** use different configuration files.

---

### Post by esaym on 2006-11-18
Thanks for helping.  As far as I know this is what I have to work with: [[img]http://la.gg/thmb/snapshot4.png[/img]]("http://la.gg/v/snapshot4.png")

Folder config file doens't seem to helpful either: [http://kate-editor.org/article/.kateconfig](http://kate-editor.org/article/.kateconfig)

---

### Post by CatKiller on 2006-11-18
So untick the **Local files** box (if this is the configuration for normal kate). Then run **kdesu kate** and look at the options there. Are they different?

---

### Post by esaym on 2006-11-18
Ohhhh I follow.  I just checked and yes they are different!!  Smart man!

---

### Post by CatKiller on 2006-11-18
One does one's best :)

Glad it worked for you.

---

### Post by CatKiller on 2006-11-18
btw, you might find [this page]("http://psychocats.net/ubuntu/graphicalsudo") helpful.

---

