---
title: "I can't disable the Shfit+Backspace please help"
date: 2006-12-14
forum: General Help
---

### Post by Kanybus on 2006-12-14
Ok, I've tried 3-4 different suggestions on the forums for disabling the shift+backspace restart.  None of them work for me thus far!  Please can anyone help, I really don't want to have to go back to windows on my laptop but if I can't fix this, i'm going to have to.](*,) 
And please don't assume I know what you are talking about :)  Took me a week to figure out how to make a script lol so the first walk through took the longest.  I still don't know if i'm doing it write so be complete please.

---

### Post by Kanybus on 2006-12-22
bump

---

### Post by iamhugeinjapan on 2006-12-22
Open a Terminal and put this in:

```
xmodmap -e "keycode 22 = BackSpace"
```

Then press Shift+Backspace

If you don't get logged out,  go to Systems - Preferences - Sessions then the Startup Programs tab. Click 'Add' and paste in the text I gave you. You shouldn't get logged out anymore.

---

