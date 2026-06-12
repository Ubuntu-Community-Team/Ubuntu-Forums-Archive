---
title: "Beryl and xmodmap"
date: 2006-10-03
forum: General Help
---

### Post by brechtvb on 2006-10-03
When i start my gnome, beryl is properly loaded. But i have a belgian keyboard, therefor, i need to use alt gr for putting an euro-symbol or cornered brackets, etc...

when i do:
```
xmodmap /usr/share/xmodmap/xmodmab.be
```

Typing goes fine, but i can't use the application switcher anymore, like alt-tab.

I checked the keyoutput before and after i used xmodmap with xev, both times the same output

How can i fix this

---

### Post by yugo on 2006-10-03
After starting beryl, I have also problems with my keyboard. I just type setxkbmap to use my X config. I suppose your command does the same, and I won't be usefull

---

### Post by brechtvb on 2006-10-03
```
setxkbmap be
```

did the trick, thank you very much

(and i was trying loads of options ..)

---

### Post by Jenda on 2006-11-15
Have a look if this helps: [http://ubuntuforums.org/showthread.php?t=201020](http://ubuntuforums.org/showthread.php?t=201020)

---

