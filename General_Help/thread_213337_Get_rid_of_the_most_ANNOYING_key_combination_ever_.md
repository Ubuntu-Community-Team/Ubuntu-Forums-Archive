---
title: "Get rid of the most ANNOYING key combination ever? (Ctrl + backspace)"
date: 2006-07-11
forum: General Help
---

### Post by krazykirk on 2006-07-11
Hi everyone,

I keep pressing Ctrl + Backspace when I'm typing (usually here on the forums) and It logs me out! It's extremely fustrating and I would really like to fix it.

From my research, I found that this error only occurs on XGL (which i use).

I found a method before, this script:

```

gnome-window-decorator &  compiz --replace gconf decoration wobbly fade minimize cube rotate zoom scale move resize place switcher &
xmodmap /usr/share/xmodmap/xmodmap.<language> 
```

and it works fine, but it disables most of the compiz effects, such as the cube.

Any ideas anyone?

---

### Post by RAOF on 2006-07-11
Run a more recent version of XGL?  **My** XGL server doesn't die with that key-combination anymore, and I'm not using an xmodmap line.

For your edification, the version I'm using is: 7.0.0+cvs20060625

---

