---
title: "Anybody cracked the 15 sec solid colour wait after login"
date: 2008-05-29
forum: General Help
---

### Post by philinux on 2008-05-29
I've put a splash screen in and set the colour to match the theme. But this is what I get after login window.

7 sec solid colour full screen
1 sec picture
7 sec solid colour full screen

Desktop.

---

### Post by Forlong on 2008-05-30
The second time the desktop disappears is because of Compiz.
If it bothers you that much, you could delay its start but there's no way to get rid of it completely for now.

---

### Post by philinux on 2008-05-30
I only get the desktop after the 15 second delay.

I've got rid of the picture now and set background colour to black.

So now after the login window I get 15 seconds of blackness....

---

### Post by philinux on 2008-06-05
Bump

---

### Post by jpeddicord on 2008-06-05
There's no way around it; it's just loading everything necessary for your desktop. As Forlong said, the second disappearance is because Compiz is starting up. If you disable Compiz (System > Preferences > Appearance; Visual Effects) you might see a slight login time decrease but you will also lose your desktop effects.

---

### Post by philinux on 2008-06-06
Why cant the system have the choice to show a pic while we wait?

---

### Post by Forlong on 2008-06-06
There is:
```
gconftool-2 -s -t bool /apps/gnome-session/options/show_splash_screen true
```

It has been removed by Ubuntu for two reasons:
1) it's inconsistent with Compiz by default
2) on some machines, it takes longer to show the splash screen then it would take to actually boot without it

---

