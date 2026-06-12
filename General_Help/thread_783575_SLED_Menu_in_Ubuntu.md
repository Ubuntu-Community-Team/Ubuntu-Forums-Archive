---
title: "SLED Menu in Ubuntu"
date: 2008-05-05
forum: General Help
---

### Post by motang on 2008-05-05
Hello, I run Ubuntu on my desktop and laptop.  I have a 15.4" laptop, and I was wonder on how to have a better way to have more real estate on my screen and I got to thinking how to have the menu SLED and OpenSUSE come with.  After a bit of searching I found out how to do.  One thing is the forums didn't have anything on it, so here is my post.

So in order for you to get the menu go into the terminal and type in:

> sudo apt-get install gnome-main-menu

Now go into the "Add to panel..." which is found when you right click on the panel and choose "Main Menu: Default menu and application browser"
But make sure you **remove** your other Main Menu **before** adding the SLED Menu.


Note: I don't take any type of credit for this as I found out how to get the menu from this [site]("http://hackerslife.blogspot.com/2006/07/sled-menu-for-ubuntu-uslab-now-in-repo.html"), and I am very thankful for it.  :)

---

### Post by mano cazalet on 2008-05-05
it is so good to have so many options :)

here goes another one

sudo apt-get install gimmie

and looks like this:

---

### Post by JacksonDane on 2008-05-10
Not having any luck here, it just adds a black line

---

### Post by motang on 2008-05-10
I ran into that make sure you remove the current one first.  I was to resolve that issue by removing the current one and then adding the "SLAB" Menu.  I hope this solves your problem. :-)

---

### Post by rogerdean on 2008-08-19
best SLED-like menu i've found is pinched from Linux Mint - you can pick it up here

[http://www.linuxmint.com/repository/pool/daryna/m/mintmenu/mintmenu_3.2_i386.deb](http://www.linuxmint.com/repository/pool/daryna/m/mintmenu/mintmenu_3.2_i386.deb)

the icon is /usr/share/pixmaps/mintmenu.png so you can replace that with an ubuntu icon or whatever you like

---

### Post by ravenvii on 2008-08-19
There's also the Ubuntu System Panel (USP), [here](http://code.google.com/p/ubuntu-system-panel/), which is what Linux Mint uses.

---

