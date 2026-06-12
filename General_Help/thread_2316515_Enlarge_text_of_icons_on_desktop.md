---
title: "Enlarge text of icons on desktop"
date: 2016-03-08
forum: General Help
---

### Post by Camilia on 2016-03-08
I would like to enlarge the text under the icons on desktop. Any suggestions, please explain.

I tried resizing and that just affects the icon. 
Opened Universal Access and select the Seeing tab. Switched Large Text to ON. 
Downloaded tweek tool. Resized the fonts.

---

### Post by howefield on 2016-03-08
If you don't mind the command line, you could try

```
gsettings set org.gnome.nautilus.desktop font 'Ubuntu 8'
```

'Ubuntu 8' is the font and size - substitute with whatever you want it to be.

---

