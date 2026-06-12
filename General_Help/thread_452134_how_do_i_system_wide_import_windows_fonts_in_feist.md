---
title: "how do i system wide import windows fonts in feisty ?"
date: 2007-05-23
forum: General Help
---

### Post by kraymore on 2007-05-23
how do i system wide import windows fonts in feisty ? 

danke

---

### Post by Bachstelze on 2007-05-23
Doesn't Gnome have a font manager that will let you do that ? KDE has one...

---

### Post by PlatoDan on 2007-05-23
The easiest way I've seen is to make a new directory in your home folder named ".fonts" and adding any fonts you want there. 

If your windows partition is mounted you can just copy and paste from C:/Windows/Fonts into /home/(your name)/.fonts

Hope this helps. :)

---

### Post by Bachstelze on 2007-05-23
That won't install them system-wide...

---

### Post by BrowneR on 2007-05-30
First get root:
```

sudo -s

```

Create a directory to hold the fonts (as root):
```

mkdir /usr/share/fonts/truetype/msfonts

```

Copy the font(s) into the newly created directory:
```

cp [fonts] /usr/share/fonts/truetype/msfonts

```

Run the following to recreate the font cache:
```

fc-cache -f -v 

```

---

