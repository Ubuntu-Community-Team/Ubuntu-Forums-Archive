---
title: "workaround for nautilus and fluxbox"
date: 2007-06-27
forum: General Help
---

### Post by zenflux on 2007-06-27
Hello all, 

If this question is answered in another post do forgive me, and pass a link please. :)

I am running feisty with fluxbox and I noticed that using nautilus to browse files breaks the fluxbox menu. I do love the CLI but I was wondering if there was a workaround so that I could use nautilus without it crashing fluxbox. 

On a side note, Ubuntu is just beautiful ! Good work people !

benjamin

---

### Post by RedSquirrel on 2007-06-27
You need to run nautilus with the **--no-desktop** option so that it doesn't manage the desktop.

```
nautilus --no-desktop
```

---

