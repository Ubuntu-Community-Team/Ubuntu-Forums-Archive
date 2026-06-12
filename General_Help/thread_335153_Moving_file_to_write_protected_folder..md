---
title: "Moving file to write protected folder."
date: 2007-01-09
forum: General Help
---

### Post by DMAthlon on 2007-01-09
I need to move "/home/collin/Desktop/Tahoma.ttf" to "/usr/share/wine/fonts" which is write protected. how do i do it in console, I assume "sudo ....." and i'm lost from there. thanks.

---

### Post by vf514 on 2007-01-09
I would assume that

```
sudo cp ~/Tahoma.ttf /usr/share/wine/fonts/
```

would work. If not, please post the output of that command.

---

### Post by hikaricore on 2007-01-09
> **vf514 said:**
> I would assume that

```
sudo cp ~/Tahoma.ttf /usr/share/wine/fonts/
```

would work. If not, please post the output of that command.

I think you mean:

```
sudo cp ~/Desktop/Tahoma.ttf /usr/share/wine/fonts/
```

---

### Post by majoridiot on 2007-01-10
or

```
sudo nautilus
```

to bring up the gui to cut and paste it. :D

---

### Post by Iowan on 2007-01-10
or **sudo mv ...** to move instead  of copy.

---

