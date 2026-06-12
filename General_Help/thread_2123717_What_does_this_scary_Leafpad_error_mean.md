---
title: "What does this scary Leafpad error mean?"
date: 2013-03-08
forum: General Help
---

### Post by gotnexusbluz on 2013-03-08
[COLOR=#222222][FONT=Verdana]I've been puzzling all day over a different, and vexing problem, for which solutions that were offered involved scripts created with Leafpad. Now I don't even know if Leafpad even works for me! What is this error, which I get every time I try and use it in any way (with or without opening or creating a new file)?[/FONT][/COLOR]
```

[COLOR=#222222][FONT=Verdana]** (leafpad:2839): WARNING **: Invalid borders specified for theme pixmap:[/FONT][/COLOR]
[COLOR=#222222][FONT=Verdana]        /usr/share/themes/Lubuntu-default/gtk-2.0/images/null.png,[/FONT][/COLOR]
[COLOR=#222222][FONT=Verdana]borders don't fit within the image[/FONT][/COLOR]

```
[COLOR=#222222][FONT=Verdana]I first noticed it after trying to create an image in a hidden folder. Leafpad didn't have a problem opening a new file for creation there, but it would not display anything hidden in the Save As window! Do I need to reinstall?[/FONT][/COLOR]

---

### Post by oldos2er on 2013-03-08
According to [this]("http://askubuntu.com/questions/225093/emacs-gives-warnings-in-lubuntu") I'd check to see if the package lubuntu-artwork is installed.

---

### Post by gotnexusbluz on 2013-03-08
> **oldos2er said:**
> According to [this]("http://askubuntu.com/questions/225093/emacs-gives-warnings-in-lubuntu") I'd check to see if the package lubuntu-artwork is installed.

It is installed...and I was close to being sold on this LXDE flavor!

---

### Post by vasa1 on 2013-03-08
IMO, you don't have to do anything! If you go by the errors one sees by launching programs from the terminal, many programs, not just Leafpad, will have to be junked. While I agree that errors should not be there, these errors are insignificant.

---

### Post by 3rdalbum on 2013-03-08
It is not an error, only a warning. GTK-based programs typically throw up a lot of minor warnings. Don't worry about them, they are not causing any problems.

---

