---
title: "Plank Themes"
date: 2013-02-13
forum: General Help
---

### Post by Bulletrulz on 2013-02-13
So i installed plank you know and went online to see if theming was possible and to my joy it was so i got the theme and was gonna put it in .config/plank/themes but to my suprise that wasent there i made it in that place but the theme wont work does anyone know how to fix this

---

### Post by Frogs Hair on 2013-02-13
The method at the link doesn't mention a themes folder but it does mention pasting directly to the plank folder. ?   [http://www.omgubuntu.co.uk/2012/03/3-themes-for-linux-dock-plank](http://www.omgubuntu.co.uk/2012/03/3-themes-for-linux-dock-plank)

---

### Post by Enigmapond on 2013-02-13
Well first you need to make sure that the theme is one that will work with your version of GTK. (I have no idea what distro you are using). If it is. open your home folder, do CTRL H to show hidden files. Look for a folder named .themes. If none there, create one insuring that it begins with a (.) then just put the theme folder in there. Hope this helps.

Cheers!

---

### Post by brainwash on 2013-02-13
If you are using a recent version of plank, you will have to move the theme files here:
```
/home/<user>/.local/share/plank/themes
```

---

### Post by Bulletrulz on 2013-02-13
> **brainwash said:**
> If you are using a recent version of plank, you will have to move the theme files here:
```
/home/<user>/.local/share/plank/themes
```

i did this but the theme did not change still

---

### Post by brainwash on 2013-02-13
So, the downloaded theme is located here:
```
/home/<user>/.local/share/plank/themes/<theme name>/
```

Did you change the following entry in the config file?
```
/home/<user>/.config/plank/dock1/settings
```
```
#The name of the dock's theme to use.
Theme=<theme name>
```

---

### Post by Bulletrulz on 2013-02-13
> **brainwash said:**
> So, the downloaded theme is located here:
```
/home/<user>/.local/share/plank/themes/<theme name>/
```

Did you change the following entry in the config file?
```
/home/<user>/.config/plank/dock1/settings
```
```
#The name of the dock's theme to use.
Theme=<theme name>
```

no ill do that do i just put there the location of where its at?

---

