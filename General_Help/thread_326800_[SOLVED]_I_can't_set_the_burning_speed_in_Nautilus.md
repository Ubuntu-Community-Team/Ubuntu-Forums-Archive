---
title: "[SOLVED] I can't set the burning speed in Nautilus"
date: 2006-12-28
forum: General Help
---

### Post by siddartha on 2006-12-28
Hello,

I have a very disturbing problem. No matter what I try I can't seem to get access to that option in nautilus burner about the speed. It is grayed out and set on maximum speed. I used gconf-editor and still no results. What else can I try?

---

### Post by wpshooter on 2006-12-28
My suggestion would be that you install and use the K3b program as a CD burner.

---

### Post by logos34 on 2006-12-28
yeah, use k3b...it has 'verify and a ton of other options.


$ sudo gconf-editor

does that allow you to edit it?

---

### Post by siddartha on 2006-12-28
sudo gconf-editor does let me modify the value from 0 to 16 but it has no effect even if I log off than relog in.

---

### Post by shrimphead on 2006-12-28
or try gnomebaker or graveman, they are slightly less feature packed than K3b but they do their job admirably and they are gtk based apps so don't require loading oodles of KDE dependancies

---

### Post by siddartha on 2007-01-28
gnomebacker, althouth it has a cute interface, has lots of missing features. In the early Summer of 2006 I tested it with Dapper and that version was unable to handle overburning for example. So if my iso file would be 700M plus 1k it wouldn't burn. k3b works well on the other hand and alreayd tested it with an external DVD unit. The version from Dapper couldn't show the internal buffer. The one from Feisty can do that too so k3b is for me the way to go.

---

### Post by siddartha on 2007-10-16
K3B is the answer. nautilus cd burning pack is the wrong solution. And it still depends on a dummy pack (cdrecord) as of Feisty.

---

