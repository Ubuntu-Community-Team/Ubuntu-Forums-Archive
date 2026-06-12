---
title: "artsd process"
date: 2007-03-03
forum: General Help
---

### Post by xenoalien on 2007-03-03
Anyone know what the artsd process is? It is slowing down my computer. I am not ablle to disable or kill the process because it comes back. I can only set the priority on low but it still takes a major bite out of my cpu power. It was taking 80-90% of my amd 3000+ CPU now it is at 40%.

---

### Post by 3rdalbum on 2007-03-04
I don't know why artsd is running on your computer, unless you have a KDE program running.

Artsd is a kind of sound server for KDE programs; i.e. it manages the use of the sound card and shares it between programs.

If you don't use KDE programs, you can remove it through:

```
sudo apt-get remove --purge arts
```

---

