---
title: "How to install arabic font?"
date: 2008-05-13
forum: General Help
---

### Post by reyhan on 2008-05-13
Hello can i Install Arabic font on open office?...
Because i need it For my School project....:(:(

---

### Post by Brucevdk on 2008-05-18
Using language support (*System -> Administration -> Language Support -> Arabic*) you'll be able to change the input method. I also use the Win key to switch between groups, see *System -> Preferences -> Keyboard -> Layout Options -> Group Shift/Lock behavior -> Left Win-key changes group*. The Arabic glyps themselves seem to be installed through ttf-arabeys, see:
```
$ dpkg -L ttf-arabeyes
/usr/share/fonts/truetype/ttf-arabeyes/ae_AlArabiya.ttf
/usr/share/fonts/truetype/ttf-arabeyes/ae_AlBattar.ttf
/usr/share/fonts/truetype/ttf-arabeyes/ae_AlHor.ttf
[...]
```

---

