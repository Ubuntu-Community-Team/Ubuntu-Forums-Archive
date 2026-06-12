---
title: "How do I install the SLED menu"
date: 2007-03-30
forum: General Help
---

### Post by Espreon on 2007-03-30
How do I install it in Feisty Fawn. The SLED MENU is that menu in openSUSE GNOME

Picture: [http://en.opensuse.org/Image:Start_menu.jpg](http://en.opensuse.org/Image:Start_menu.jpg)

---

### Post by Schalken on 2007-03-30
Install the package gnome-main-menu
```
sudo apt-get install gnome-main-menu
```

---

### Post by Espreon on 2007-03-30
And then what?

---

### Post by Schalken on 2007-03-30
And then right click on the panel > Add to Panel > Search for "main menu" or something

---

### Post by Espreon on 2007-03-30
It does not look anything like the one in the picture.

---

### Post by Schalken on 2007-03-30
You may have added the one called "main menu" thats actually just a simgle button menu, its not that one, its another. ill install it and see what its actually called in the add to panel dialog

---

### Post by Espreon on 2007-03-30
Oh.

---

### Post by Schalken on 2007-03-30
log out and log back it, then do the add to panel, and its there with a computer icon.

---

### Post by Espreon on 2007-03-30
Thanx. It is great!

---

### Post by Espreon on 2007-03-30
Now how do I remove the default crap?

---

### Post by Smuve on 2007-03-30
Right click the item on the panel, Remove from Panel.

---

### Post by mech7 on 2007-03-30
Is there anyway to change the icon / text? And the amount of applications in the menu?
Also how do i adde seperators like the default panels on top with the little dots? And how do i get my wireless to show there? :)

---

### Post by herbster on 2007-03-30
I dig that menu, can it be installed on Edgy? I'm using GNOME.

---

### Post by nchase on 2007-03-30
> **herbster said:**
> I dig that menu, can it be installed on Edgy? I'm using GNOME.

did you try ```
sudo apt-get install gnome-main-menu
```

That worked for me.

---

### Post by herbster on 2007-03-30
Oh my, this menu is reeeally nice and clean, and so well laid-out. Kicks the Start Menu's booty IMO. Might replace my longtime bottom panel!!

---

### Post by mech7 on 2007-04-20
> **mech7 said:**
> Is there anyway to change the icon / text? And the amount of applications in the menu?
Also how do i adde seperators like the default panels on top with the little dots? And how do i get my wireless to show there? :)

nobody knows this? :(

---

### Post by mariner09 on 2007-04-30
There are currently 2 different forks of gnome-main-menu.

One is edited by gconf and the other is not.

When your wireless is active it should be listed in the system-are to the right.

I'm not sure what you mean by dots.

---

