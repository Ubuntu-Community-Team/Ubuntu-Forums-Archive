---
title: "issues with creating wine program desktop shortcuts"
date: 2013-08-09
forum: General Help
---

### Post by steve8 on 2013-08-09
Hi havin a problem with creating desktop shortcuts for wine apps. It fails to initialize. I'm thinking it has something to do with it being a portible version and not installed to wine directory but here is leaf pad commands for call of duty:

[Desktop Entry]
Name=Call of Duty
Exec=wine  "/home/simon/Games/Call of Duty/CoDSP.exe"
Icon=/home/simon/Picture/Icons/Games/PC/Shooters/codww_icon.png
Terminal=false
Type=Application
StartupNotify=true
Comment=Launch CoDSP.exe

---

### Post by DuckHook on 2013-08-10
You would probably attract better replies from the WINE experts by posting in the WINE subforum, but from a non-expert, it seems to me that your *Exec* line should read:```
Exec=wine C:\\\\windows\\\\command\\\\start.exe /Unix /home/simon/Games/Call of Duty/CoDSP.exe
```This assumes that your path to the the game directory is correct and that you have a default WINE install. If you have installed into a WINE prefix (which is not a default install), then you must define the prefix.

Note that I am not even remotely a WINE expert. Guru input is welcome. I could certainly use the learning.

---

### Post by steve8 on 2013-08-10
no that gave me an error: File not found

---

### Post by DuckHook on 2013-08-10
Rats. Forgot to escape the spaces in your path. Try:```
Exec=wine C:\\\\windows\\\\command\\\\start.exe /Unix /home/simon/Games/Call\\ of\\ Duty/CoDSP.exe
```

---

### Post by steve8 on 2013-08-10
hell ye that seemed to do it....thanks

---

### Post by DuckHook on 2013-08-10
Glad it worked out. To help others, please remember to mark this thread "solved".

---

