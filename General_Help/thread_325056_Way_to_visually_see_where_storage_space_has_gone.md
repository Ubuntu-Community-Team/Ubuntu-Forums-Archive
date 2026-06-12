---
title: "Way to visually see where storage space has gone?"
date: 2006-12-24
forum: General Help
---

### Post by Jbloudg20 on 2006-12-24
Is there a visual (via graph, chart, even table) way to see where the largest files on the hard drive are? I have a 25 gig partition for my Hoary install, and I ran out of space earlier today. I know in windows there are tools to be able to view where this space is going, can I do the same in Ubuntu? Thanks!

---

### Post by cilynx on 2006-12-24
There's the ever popular:
```

cd / && sudo du -hs *

```

---

### Post by theh3brewhammer on 2006-12-25
Check out [Baobab]("http://www.marzocca.net/linux/baobab.html#installation").

It's part of gnome-utils, so run:
```

sudo apt-get install gnome-utils

```

And then type 
```

baobab

```

Hope this is what you are looking for.

---

### Post by mexlinux on 2006-12-25
konqueror comes with that option by default.
Simply chose FSview as view mode.

---

### Post by Klin'Targ on 2006-12-25
I've tried a few programs that can do this. My current favorite is a Java program called jDiskReport ([http://www.jgoodies.com/freeware/jdiskreport/]("http://www.jgoodies.com/freeware/jdiskreport/"))

If Java isn't your thing, or you want to keep your system free of non-open source software, try Filelight (pictures at [http://www.methylblue.com/filelight/]("http://www.methylblue.com/filelight/")), which is a KDE program which does a similar thing and is in the repositories.

---

