---
title: "ok, I'm blind"
date: 2004-10-31
forum: General Help
---

### Post by negativ on 2004-10-31
I KNOW (I think) that I saw an option somewhere to disable the animation associated with minimizing windows to the panel.  I now want to do this, and can't figure out where it was.

---

### Post by Joeb on 2004-10-31
[QUOTE=negativ]I KNOW (I think) that I saw an option somewhere to disable the animation associated with minimizing windows to the panel.  I now want to do this, and can't figure out where it was.[/QUOTE]


Not sure if this is what you're looking for, but if you go to the GConf editor (Applications==>System tools==>Configuration Editor) and then under desktop, select gnome and then interface, there is an option called enable_animations.  Uncheck it and see if that does the trick.

Joeb

---

### Post by homerhomer on 2004-11-01
also while in gconf-editor you can now search for a string.  I did a search for animation and check the box below for searching strings

Hope this helps

---

### Post by FLeiXiuS on 2004-11-01
[QUOTE=negativ]I KNOW (I think) that I saw an option somewhere to disable the animation associated with minimizing windows to the panel.  I now want to do this, and can't figure out where it was.[/QUOTE]


Yes there is a way...

Applications > System Tools > Configuration Editor

From there:

Apps > Metacity > General

Check off 'reduce_resources'

This should be what your looking for.

---

