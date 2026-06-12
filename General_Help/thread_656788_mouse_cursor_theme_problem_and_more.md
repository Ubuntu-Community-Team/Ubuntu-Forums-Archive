---
title: "mouse cursor theme problem and more"
date: 2008-01-02
forum: General Help
---

### Post by nagla on 2008-01-02
i am running gutsy gibbon and when i change the mouse theme it changes but not when being used on the desktop. for example when i change the theme to the black theme, over the desktop and panels it turns white. then when i am over a firefox window or amsn window it turns black again. anyone have a fix for this? i have a gma950 if that makes a difference.

also after gdm there is no splash screen for some reason, plus my background color was changed to black a long time ago but after gdm it still flashes the beige ubuntu color before my background image appears. 

thanks in advance, and good job to ubuntu developer :)

---

### Post by PurposeOfReason on 2008-01-02
Are you using compiz? If so, there is a cursor there that might be at fault. However, it's probably easier to create a file cale ~/.Xdefaults and put something like this in it. Case sensitive.
```
Xcursor.theme: simpleandsoft
```

---

### Post by jayde6 on 2008-01-02
Like Purpose of Reason said, it is probably because of compiz. If you have the "Compizconfig-settings-manager" installed, go into general options and clear the box that says "Cursor theme". As far as the gdm screen is concerned here is a tutorial that will help you remove the beige.

[http://bapoumba.wordpress.com/2007/10/24/change-gdm-background-color-to-match-your-gdm-theme-applies-to-xfce](http://bapoumba.wordpress.com/2007/10/24/change-gdm-background-color-to-match-your-gdm-theme-applies-to-xfce)

Hope this helps,
~Jennifer

---

### Post by funnypanks on 2008-01-03
jayde6 thanks so much, you hit the nail on the head and after doing what you suggested ubuntu is everything i ever wanted, and more lol.
this prob had been bothering me since early feisty fawn

---

