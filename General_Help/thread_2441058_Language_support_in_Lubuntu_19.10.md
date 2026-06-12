---
title: "Language support in Lubuntu 19.10"
date: 2020-04-18
forum: General Help
---

### Post by knaytmar on 2020-04-18
Good morning. I just installed Lubuntu 19.10 and I can't found language support option anywhere. In older versions it was in preferences tab in lubuntu menu but now I searched everywhere and can't change language. Maybe someone know how to do it.

---

### Post by #&amp;thj^% on 2020-04-18
See if this helps:
```
sudo apt install $(check-language-support)
```

---

### Post by GhX6GZMB on 2020-04-18
Keyword is "locale" and "FciTx" in the Applications Menu.

---

### Post by knaytmar on 2020-04-18
[COLOR=#000000]"locale" and "FciTx" is only changing keyboard layout and some country related stuff not interface language.
I also tried [/COLOR][COLOR=#000000][FONT=&amp]sudo apt install $(check-language-support) but still I can't change it anywhere.
[/FONT][/COLOR]

---

### Post by #&amp;thj^% on 2020-04-19
After the install did you run:
```
check-language-support
```
"check-language-support"  =  returns  the  list  of  missing  packages in order to provide a complete language environment.
Also might be useful, "-a, --all" check all available languages.
For more please read: "man check-language-support"

---

