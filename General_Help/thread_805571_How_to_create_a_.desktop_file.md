---
title: "How to create a .desktop file?"
date: 2008-05-24
forum: General Help
---

### Post by chunchengch on 2008-05-24
I am still learning how to create deb file, one problem I am facing now is I can not find relative materials to create a .desktop file, so can anyone post here the format of .desktop file or something else useful? thanks for your help!

---

### Post by angry_johnnie on 2008-05-24
Look inside /usr/share/applications.

There's lots of .desktop files in there.

I'm not sure it will allow you to open them with a regular text editor, like gedit.  But you can open them with nano, or just look at them with cat, or better yet, less.

open a terminal, and type this:

```
cat /usr/share/applications/yelp.desktop
```

or, if you prefer

```
less /usr/share/applications/yelp.desktop
```

And it will let you see the .desktop file for yelp.

You can then take from it what you feel is necessary.

It's, really, not that difficult, once you've seen how other .desktop files have been written.

Good luck.

---

### Post by chunchengch on 2008-05-24
angry_johnnie,

Thanks!

---

### Post by chrisccoulson on 2008-05-24
Have a look here too: [http://library.gnome.org/admin/system-admin-guide/stable/menustructure-desktopentry.html.en]("http://library.gnome.org/admin/system-admin-guide/stable/menustructure-desktopentry.html.en")

Definately look around some of the .desktop files on your system as well though, as there are lots of fields used which aren't explained in the GNOME System Administration Guide (such as StartUpNotify)

---

### Post by chunchengch on 2008-05-24
> **chrisccoulson said:**
> Have a look here too: [http://library.gnome.org/admin/system-admin-guide/stable/menustructure-desktopentry.html.en]("http://library.gnome.org/admin/system-admin-guide/stable/menustructure-desktopentry.html.en")


chrisccoulson,

Great! this is really what I want, thanks a lot!

---

