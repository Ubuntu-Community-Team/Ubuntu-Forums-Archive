---
title: "How Do You Change Default File Manager In Ubuntu MATE?"
date: 2015-06-15
forum: General Help
---

### Post by joel36 on 2015-06-15
I've been trying to change the default manager, but nothing has helped. Used exo-preferred-applications, didn't work. Tried MATE tweak, but doesn't give an option that I could find

---

### Post by dolphintweety on 2015-06-15
[FONT=lucida console][SIZE=5][COLOR=#444444]Did you try to run in terminal the command [/COLOR][/SIZE]**[SIZE=5]mate-default-applications-properties[/SIZE]**[SIZE=5]?[/SIZE]
[SIZE=4]Sorry in case you tried that already [/SIZE][/FONT][CENTER][COLOR=#000000]:|[/COLOR][/CENTER][FONT=lucida console][SIZE=4].[/SIZE]
[/FONT]

---

### Post by Dennis N on 2015-06-15
You already have the best file manager in Caja. But, if you are adamant, I would recommend asking Mr. Wimpress, the Ubuntu MATE project leader. If you post on the MATE discussion forum:

[https://ubuntu-mate.community/](https://ubuntu-mate.community/)

you will get his attention.

---

### Post by kerry_s on 2015-06-15
> **joel36 said:**
> I've been trying to change the default manager, but nothing has helped. Used exo-preferred-applications, didn't work. Tried MATE tweak, but doesn't give an option that I could find

dconf-editor-> org-> mate-> desktop-> session

under required-componets-list take out the 1 you want to replace. you just want to prevent it from loading as your going to add your own to startup applications.

under required-componetes blank out the 1 you want to replace.

i replaced my mate-panel with xfce4-panel, you just have to do it for caja.

pics of steps

(if your wondering why i didn't put xfce4-panel in there, is because from there it wouldn't load)

---

