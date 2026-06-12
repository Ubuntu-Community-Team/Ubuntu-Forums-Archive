---
title: "Wine Issues"
date: 2007-04-02
forum: General Help
---

### Post by Madmoose on 2007-04-02
Hello again, 

Today I have three issues:

> Is *.wine* a hidden folder, and if so how do I view hidden folders. If not, where in the world is .wine? I need to place some .dll's, and every tutorial tells me to go into .wine. I can't find it anywhere!

> I've noticed that the only program that has sound, sometimes, is Starcraft. Yet, I can't seem to get sound out of any other program. Does anyone know how to fix this?


> Does anyone know why wine crashes when I try and log online with it. I.E. battlenet

---

### Post by chewearn on 2007-04-02
.wine directory is in your user's home.  It hidden, so you need to enable "Show Hidden Files" in Nautilus to see it.

```
defaultuser@defaultuser-desktop:~$ cd .wine
defaultuser@defaultuser-desktop:~/.wine$ ls
dosdevices  drive_c  system.reg  userdef.reg  user.reg
defaultuser@defaultuser-desktop:~/.wine$ 

```

Don't know about the other questions.

---

### Post by Madmoose on 2007-04-02
> **AstalaVista said:**
> .wine directory is in your user's home.  It hidden, so you need to enable "Show Hidden Files" in Nautilus to see it.

```
defaultuser@defaultuser-desktop:~$ cd .wine
defaultuser@defaultuser-desktop:~/.wine$ ls
dosdevices  drive_c  system.reg  userdef.reg  user.reg
defaultuser@defaultuser-desktop:~/.wine$ 

```


Now, I did that code and it didn't do anything. Filling out that code will Show Hidden Files, and if not where do you find the Nautilus menu?

---

### Post by chewearn on 2007-04-02
Sorry about the code.  It was not meant for copy/pasting.

When you open Nautilus in home directory; then, Menu > View > Show Hidden Files.   Or shortcut key is CTRL+H.

You will suddenly see a lot of hidden directories and files appearing (they started with dot character)

---

### Post by zvacet on 2007-04-02
[http://doc.gwos.org/index.php/HowToWine]("http://doc.gwos.org/index.php/HowToWine")

---

### Post by Madmoose on 2007-04-02
> **AstalaVista]Sorry about the code. It was not meant for copy/pasting.

When you open Nautilus in home directory said:**
> 

Sweet thanks! 

[QUOTE=zvacet]http://doc.gwos.org/index.php/HowToWine

I've been looking around for a good URL! Thanks!

---

