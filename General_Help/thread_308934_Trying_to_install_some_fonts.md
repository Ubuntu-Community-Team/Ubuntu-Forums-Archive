---
title: "Trying to install some fonts"
date: 2006-11-28
forum: General Help
---

### Post by tee2 on 2006-11-28
I'm trying to install some windows fonts using [this]("http://www.linux.org.mt/article/ttfonts") as a guide.

I'm up to the "Telling XWindows about your fonts" part and I'm stuck here
```
tee@tee-laptop:/usr/local/fonts/ttf$ ttmkfdir > fonts.scale
bash: fonts.scale: Permission denied
tee@tee-laptop:/usr/local/fonts/ttf$ sudo ttmkfdir > fonts.scale
bash: fonts.scale: Permission denied

```

As you can see I tried using sudo but it did nothing. What do I need to do to be able to use these commands?

---

### Post by Joe_CoT on 2006-11-28
See this how to:

[http://penguinfonts.com/howto/ubuntu.php](http://penguinfonts.com/howto/ubuntu.php)
You basically move the fonts into a font directory and re-cache them.

---

### Post by tee2 on 2006-11-28
apparently I already have msttcorefonts installed, but it doesn't include "terminal" which is what I really need.

---

