---
title: "disable users from editing menus"
date: 2008-02-27
forum: General Help
---

### Post by keenboy on 2008-02-27
Is it possible to stop non admin users to from editing menus?

The best possible solution for this would be to disable the 'right click' function from the menu panel. Is this possible?

I have installed pessulus. This doesn't include this feature.](*,)

I have also installed sabayon but it's full of bugs and keeps crashing.](*,)

gconf-editor also seems to lack this function.](*,)

Does anybody know the configuration area where this can be set?

Thanks

---

### Post by keenboy on 2008-02-27
In fact to achieve the same results as the 'KDE Kiosk' does would be cool! :guitar:

---

### Post by Oaf on 2008-03-11
Well, what I did was chown 700 or 744 the /usr/bin/gmenu-simple-editor,
Doesnt remove the right click option, but prevents the user from executing it.

---

