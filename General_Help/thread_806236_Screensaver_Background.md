---
title: "Screensaver Background"
date: 2008-05-24
forum: General Help
---

### Post by IllEagleAlien on 2008-05-24
I would like to embed a screen saver into my desktop as a wallpaper but I can't get it to work properly.
I am using
> kurtis@kurtis-desktop:~$ gconftool-2 --type bool --set /apps/nautilus/preferences/show_desktop false
kurtis@kurtis-desktop:~$ /usr/lib/xscreensaver/glmatrix -root
but the background doesn't do anything.

does anyone know if im doing something wrong or have another way to do it?
(I'm very new with Ubuntu so please dumb it down for me)

---

### Post by daraman2000 on 2008-05-24
Easy: instead of typing
```
kurtis@kurtis-desktop:~$ gconftool-2 --type bool --set /apps/nautilus/preferences/show_desktop false
kurtis@kurtis-desktop:~$ /usr/lib/xscreensaver/glmatrix -root 
```

type
```
kurtis@kurtis-desktop:~$ gconftool-2 --type bool --set /apps/nautilus/preferences/show_desktop false /usr/lib/xscreensaver/glmatrix -root 
```

**In one line**

Hope it helps! ;)

---

### Post by IllEagleAlien on 2008-05-25
ok I typed that in one line and it didn't work.

This is what comes up:
```
kurtis@kurtis-desktop:~$ gconftool-2 --type bool --set /apps/nautilus/preferences/show_desktop false /usr/lib/xscreensaver/glmatrix -root
Error while parsing options: Unknown option -root.
Run 'gconftool-2 --help' to see a full list of available command-line options.
kurtis@kurtis-desktop:~$ 

```

---

### Post by Forlong on 2008-05-25
Looks like you want to use **xwinwrap**, do a search in the forum how to get it and how to use it properly.

---

