---
title: "HOW to install .ttf fonts?"
date: 2007-03-02
forum: General Help
---

### Post by johann_p on 2007-03-02
I have a couple of .ttf files that I want to install into my Feisty Fawn system, but I cannot find any option in the menu that would let me do this.

These are Unicode fonts for ancient languages and I would like to work with them on my Ubuntu computer too.

---

### Post by szf on 2007-03-02
There's support (or at least, there was) in Gnome for creating a hidden folder in $HOME called **.fonts**
i.e. ```
$ mkdir ~/.fonts
$ cp ~/my-fonts-i-cant-live-without/*.ttf ~/.fonts
```

---

### Post by johann_p on 2007-03-02
Thanks! That did it!

---

### Post by gg234 on 2007-03-02
you can also try this [nice guide]("http://www.debianadmin.com/install-microsoft-corewindows-truetypeubuntu-titlemacintosh-fonts-in-ubuntu.html")

---

