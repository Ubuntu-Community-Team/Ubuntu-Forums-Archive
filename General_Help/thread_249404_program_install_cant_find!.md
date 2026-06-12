---
title: "program install cant find!"
date: 2006-09-02
forum: General Help
---

### Post by amirji on 2006-09-02
hi

i installed a program, namely stellarium coz my friend told me it was cool! but when the installation was complete, i couldnt find the application, well it wasnt on applications, where is this application residing? btw i used terminal to install. im a noobi

cheers

---

### Post by Dinerty on 2006-09-02
You may need to restart X (ctrl + alt + backspace) for it to show up, next you could try installing the debian menu, load up Synaptic Package Manager:

Search for "menu-xdg" hit "Apply" twice, this shows you alot more info on whats itnstalled.

---

### Post by ayoli on 2006-09-02
usually, apps binaries are installed in /usr/bin or /usr/local/bin, you can run your app by simply type in the name in a terminal.
if you haven't got an menu entry you can create one with alacarte menu editor (which is in menu accessoiries).

---

### Post by taurus on 2006-09-02
Open a terminal, Applications -> Accessories -> Terminal, and type

```
stellarium
```

---

