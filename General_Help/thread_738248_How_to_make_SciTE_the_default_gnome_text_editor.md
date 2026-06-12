---
title: "How to make SciTE the default gnome text editor"
date: 2008-03-28
forum: General Help
---

### Post by MountainX on 2008-03-28
Hi,

The following command can be used to set the default gnome text editor:
sudo update-alternatives --config gnome-text-editor

Unforutnately, after installing ScitTE in Ubuntu (Gutsy or Hardy) I don't get SciTE listed as an option when running the above command. Does anyone know how to fix this?

Thanks

P.S. Should I post this question in another section?

---

### Post by MountainX on 2008-03-30
bump

---

### Post by kerry_s on 2008-03-30
right click a text file> properties and set it as the default program

---

### Post by MountainX on 2008-03-30
Thanks for your reply. I should have made my question more clear. Unfortunately that solution doesn't change the definition of gnome-text-editor

I'm trying to make the change via
```
sudo update-alternatives --config gnome-text-editor
```

or via something that works at this same level

---

### Post by MountainX on 2008-03-30
Someone gave me a good idea here:
[http://www.linuxquestions.org/questions/linux-software-2/how-to-add-a-program-to-update-alternatives-631303/#post3103693](http://www.linuxquestions.org/questions/linux-software-2/how-to-add-a-program-to-update-alternatives-631303/#post3103693)

But when he claimed "I'm not really a ubuntu and/or debian-fan/-user" I thought I would wait for an answer here before trying his suggestion....

---

### Post by kerry_s on 2008-03-31
so you want to change it manually?

sudo mv /etc/alternatives/gnome-text-editor /etc/alternatives/gnome-text-editor.old
sudo ln -s /usr/bin/scite /etc/alternatives/gnome-text-editor

---

### Post by MountainX on 2008-03-31
Thanks. Very simple. If that's a recommended way, I'll do it. It certainly would accomplish my goal.

---

