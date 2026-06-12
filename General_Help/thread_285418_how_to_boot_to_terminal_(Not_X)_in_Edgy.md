---
title: "how to boot to terminal (Not X) in Edgy"
date: 2006-10-26
forum: General Help
---

### Post by branchus on 2006-10-26
Hi there

I want to boot to Terminal (not X), if I need X, I would like to input startx instead of enter X by default.

In Redhat, I can change runlevel from 5 to 3. but how can I do that in Edgy?

Thanks in advance

---

### Post by tronica on 2006-10-27
ok, pretty simple

when your in gnome, go to System -> Administration -> Services

then thumb through the list and find Graphical Login manager (gdm)

uncheck and that should do it.

---

### Post by Tambo on 2006-10-27
Can't you just remove the line in ~/.xinitrc?

---

### Post by tronica on 2006-10-27
i suppose you could, seems i remember seeing something here recently, and someone saying that edgy is different in that department.

---

