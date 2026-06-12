---
title: "How to add an option to update-alternatives --confi"
date: 2008-03-28
forum: General Help
---

### Post by MountainX on 2008-03-28
My preferred editor is not listed when I run
```
sudo update-alternatives --config gnome-text-editor
```

How do you add items to this? Thanks

---

### Post by MountainX on 2008-03-30
bump - any thoughts welcome ;)

---

### Post by leptogenesis on 2008-07-08
I'm wondering how to do this with Java, so...bump

---

### Post by leptogenesis on 2008-07-08
I figured it out-- use the --install option, as explained on this page:

[http://www.debian.org/doc/FAQ/ch-customizing.en.html](http://www.debian.org/doc/FAQ/ch-customizing.en.html)

for updating java, I used:

```

sudo update-alternatives --install /usr/bin/java java /usr/lib/jvm/jdk1.7.0/bin/java 50

```

yours ought to be something like:


```

sudo update-alternatives --install /usr/bin/gnome-text-editor gnome-text-editor /path/to/your/editor 50

```

Hope this helps.  Sorry for double-posting/necroposting (though, I guess 3 months isn't too old...)

---

