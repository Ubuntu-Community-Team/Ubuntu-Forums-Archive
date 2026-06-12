---
title: "Dumb question about terminal command"
date: 2007-02-26
forum: General Help
---

### Post by Metallinut on 2007-02-26
I have a dumb question about using ls in terminal....

In Windows, you can right-click on a folder, and in the properties, you can see how much disk space that folder (and all contents and subfolders) is using.

Is there a way to do this from inside a terminal using ls or df at all? 

for instance, if I want to see how much space ~/video/TV is using, how can I do that?  I know I can probably see it through the GUI in Nautilus or in Gnome, but I wanted to know how to do it in a terminal.

Thanks,

---

### Post by taurus on 2007-02-26
```
du -h ~/video/TV
```

---

### Post by Metallinut on 2007-02-26
> **taurus said:**
> ```
du -h ~/video/TV
```

Cool thanks.  When I first looked at the command you /code'd, I thought you were saying "Duh!"  Heh.

---

### Post by taurus on 2007-02-26
> **Metallinut said:**
> Cool thanks.  When I first looked at the command you /code'd, I thought you were saying "Duh!"  Heh.

Now, that's funny...  #-o

---

