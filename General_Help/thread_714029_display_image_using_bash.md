---
title: "display image using bash"
date: 2008-03-03
forum: General Help
---

### Post by jba6511 on 2008-03-03
what is the command to display an image using bash? I am trying to learn the command line and not use gnome but cannot find how to display an image once I have browsed to the   folder containing the image.

---

### Post by Oldsoldier2003 on 2008-03-03
> **jba6511 said:**
> what is the command to display an image using bash? I am trying to learn the command line and not use gnome but cannot find how to display an image once I have browsed to the   folder containing the image.
bash can't display the image. You would have to call an application that can display the image with the filenames as an argument.

---

### Post by jba6511 on 2008-03-03
would gimp be the default to display the image? any idea the command to use here. i do not want to edit, simply view.

---

### Post by Oldsoldier2003 on 2008-03-03
> **jba6511 said:**
> would gimp be the default to display the image? any idea the command to use here. i do not want to edit, simply view.
try this:

```
eog mypic.jpg
```

it will display the file mypic.jpg in eye of gnome i'm assuming you are running a default install of Ubuntu so eog should be installed

you can also use a path like ~/Pictures/mypic.jpg  generally anytime you specify a file in the terminal you can specify any path that you have the proper file permissions to read, write, or execute (as the situation warrants)

---

### Post by jba6511 on 2008-03-03
thanks. that worked.

---

