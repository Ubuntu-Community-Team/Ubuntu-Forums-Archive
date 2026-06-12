---
title: "pidgin"
date: 2007-09-12
forum: General Help
---

### Post by xGutsAndGloryx on 2007-09-12
I am having a hard time installing pidgin. i am getting this error msg during the ./configure command. 



configure: error:

You must have the GTK+ 2.0 development headers installed to compile Pidgin.
If you only want to build Finch then specify --disable-gtkui when running configure.

---

### Post by Nekiruhs on 2007-09-12
Why are you trying to compile it? A deb is availible [here]("http://www.getdeb.net/search.php?keywords=Pidgin")

---

### Post by DannyW on 2007-09-14
Pidgin 2.2 is out.

I cannot find a deb package for this. Anyone had any luck?

---

### Post by Peturrr on 2007-09-14
Looks like you need the Development headers of LibGTK2.
```
sudo apt-get install libgtk2.0-dev
```

---

### Post by p_quarles on 2007-09-14
```
sudo apt-get install libgtk2.0-dev
```

Once you do that, though, it's likely to give you more missing package responses. It's a pain, but you can just use apt-cache search or whatever graphical package manager to keep searching for the proper files.

---

