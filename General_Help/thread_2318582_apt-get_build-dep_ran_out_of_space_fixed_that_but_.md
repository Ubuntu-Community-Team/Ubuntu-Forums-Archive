---
title: "apt-get build-dep ran out of space fixed that but now won't install"
date: 2016-03-27
forum: General Help
---

### Post by roland-logikalsolutions on 2016-03-27
All,

I was executing this line: sudo apt-get build-dep libqt5gui5
when ran out of space. Resized with gparted, but now apt-get thinks it completed the install because it was expanding files.

How do I recover? I need to get the rest of the build-dep installed

---

### Post by grahammechanical on 2016-03-27
Have you tried the fix broken packages command?

```
sudo apt-get install -f
```

You might need to remove the package & then install again.

Regards.

---

### Post by roland-logikalsolutions on 2016-03-27
> **grahammechanical said:**
> Have you tried the fix broken packages command?

```
sudo apt-get install -f
```

You might need to remove the package & then install again.

Regards.

It was build-dep not a package. I spent about an hour trying to figure out what was missing and finally had to give up. In the morning I will wipe and start over. Seems the path of least resistance at this point. Thanks for the reply though.

---

### Post by CharlesA on 2016-03-27
You should be able to force a reinstall.

```
sudo apt-get build-dep libqt5gui5 --reinstall
```

[http://manpages.ubuntu.com/manpages/vivid/man8/apt-get.8.html](http://manpages.ubuntu.com/manpages/vivid/man8/apt-get.8.html)

---

