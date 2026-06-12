---
title: "why do we even use totem"
date: 2006-11-07
forum: General Help
---

### Post by TheRingmaster on 2006-11-07
totem can't play hardly any web content. How do I get mplayer to play videos?

---

### Post by raul_ on 2006-11-07
that's a codec problem i think

---

### Post by TheRingmaster on 2006-11-07
how do I fix this 

(that is totem by the way in the screenshot)

---

### Post by boban on 2006-11-07
> **raul_ said:**
> that's a codec problem i think

It might be... But I had some issues with totem in firefox too...

To install mplayer plugin for firefox try:
```

sudo aptitude install mozilla-mplayer 

```

---

### Post by TheRingmaster on 2006-11-07
double post sorry

---

### Post by TheRingmaster on 2006-11-07
i already have mplayer installed. I tried reinstalling and still totem plays instead

edit: the first time playing anything with totem looks like the screenshot, but the second time it plays perfect.

---

### Post by boban on 2006-11-07
> **TheRingmaster said:**
> that is what it gives me

You'll have to enable multiverse repository first. Try:

```

sudo gedit /etc/apt/sources.list

```

Find in that file lines with 'multiverse' and uncomment it (remove '#' from beginning of the line).

then

```

sudo aptitude update
sudo aptitude install mozilla-mplayer

```

---

### Post by boban on 2006-11-07
> **TheRingmaster said:**
> i already have mplayer installed. I tried reinstalling and still totem plays instead

mozilla-plugin is plugin that enable playing media with mplayer in firefox

> **TheRingmaster said:**
> 
edit: the first time playing anything with totem looks like the screenshot, but the second time it plays perfect.

So it probably missed some data while downloading...

---

### Post by dentaku65 on 2006-11-07
> **TheRingmaster said:**
> i already have mplayer installed. I tried reinstalling and still totem plays instead

edit: the first time playing anything with totem looks like the screenshot, but the second time it plays perfect.

Drastic but perfect for me:

```
sudo apt-get remove totem-xine
```
8)

---

### Post by TheRingmaster on 2006-11-07
> **dentaku65 said:**
> Drastic but perfect for me:

```
sudo apt-get remove totem-xine
```
8)
thanks that worked (but still had to reinstall mozilla-mplayer)

---

