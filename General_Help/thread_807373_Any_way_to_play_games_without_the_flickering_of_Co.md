---
title: "Any way to play games without the flickering of Compiz effects  - when it is enabled?"
date: 2008-05-25
forum: General Help
---

### Post by AaronMT on 2008-05-25
Hi.

I recently installed Wine 1.0 RC2 along with Warcraft III and everything is good except the flickering of video when Compiz effects are enabled. Do I have to disable them every time I play or can I enable a setting somewhere in the advanced options of compiz settings manager to resolve this issue?

Thanks in advance.

---

### Post by Jonne on 2008-05-25
You still have to turn compiz off manually every time. Look for compiz-switch if you want an easy launcher that can do it in one click.

---

### Post by Prospero2006 on 2008-05-25
You can always do this prior to logging in: 
```

touch ~/.config/xserver-xgl/disable

```

This will shut down your 3-d desktop and free up most of your GL resources for other apps. I find it's easiest to manage it that way in several situations. 
```

rm ~/.config/xserver-xgl/disable 

```
to re-enable compiz.

---

### Post by KuriKai on 2008-05-25
I made a script that disbles compiz then runs war3 and renables compiz after I finish war3
```

metacity --replace --sm-disable &
WINEDEBUG=fixme-all wine /home/yourhomefolder/.wine/drive_c/Program\ Files/Warcraft\ III/war3.exe -opengl
compiz --replace --sm-disable --ignore-desktop-hints ccp --loose-binding --indirect-rendering

```

---

