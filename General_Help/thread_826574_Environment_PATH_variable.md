---
title: "Environment PATH variable"
date: 2008-06-12
forum: General Help
---

### Post by ivantis on 2008-06-12
Hey guys, I need some help.
How do I change my PATH Environment variable? I have installed the bsd-games package, so for example,
```
$ tetris-bsd
```
will start the bsd-games tetris. Now, that only works locally. When I am using ssh it says "/usr/games/ is not included in the PATH environment variable". How can I change it and why does it work locally?

---

### Post by bingoUV on 2008-06-12
To add /usr/games to your PATH variable temporarily for now
```

export PATH=${PATH}:/usr/games

```

To change it permanently, add the above line to the end of ~/.bashrc. It will be set the next time you login.

What do you mean it runs locally? Do you run it from command line? Menu? Desktop icon? Panel applet? Any other way?

How do you run it when connected with ssh? Command line?

---

