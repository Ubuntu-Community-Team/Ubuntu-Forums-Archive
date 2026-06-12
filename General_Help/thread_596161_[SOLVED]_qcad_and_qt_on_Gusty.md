---
title: "[SOLVED] qcad and qt on Gusty"
date: 2007-10-29
forum: General Help
---

### Post by digitalhillbilly on 2007-10-29
Hi all,

Was wondering if any here could offer a little advice. I installed qcad a number of months back on 7.04 and not only did it work great but it looked great too. I had used 7.04 extensively and over time installed most qt components. Now I'm on a fresh Gusty install and just installed qcad again. I've installed all the seemingly appropriate qt packages but it looks like crap. 

Was wondering if any here had some pointers on which qt packages should be installed or if I have to configure something, etc.

Thanks!

dh

---

### Post by maybeway36 on 2007-10-29
Try using qtconfig.

---

### Post by digitalhillbilly on 2007-10-29
Thanks for the reply maybeway36. It seemed to me qcad is (should be) using qt4. I had installed qt4-qtconfig and ran it. the config window appeared nice and clean so it seemed qcad and qt were somehow broken. I further installed qt3-qtconfig and upon running it, it has the same blocky appearance I have with qcad. Again, my previous qcad install on 7.04 was very clean and I assumed it was using qt4. I never really paid attention to it because I just installed qcad and all the dependencies were already in place - i guess  ;)

Is there a way to set the QT version being used?

Thanks again!
dh

---

### Post by digitalhillbilly on 2007-10-29
Hello again.... just bumping my post to the top of the list cause I'm going mad! Mad I's tell ya! lol...

dh

---

### Post by digitalhillbilly on 2007-10-29
ummm... yeah. It seems maybeway36's help wzaas the ticket. I was just convinced (somehow) qcad was using qt4. After playing a bit in qtconfig it's now palatable. IIRC it was still a lot tighter in 7.04

Thanks!
dh

---

### Post by Sisophon2001 on 2007-11-18
> **digitalhillbilly said:**
> ummm... yeah. It seems maybeway36's help wzaas the ticket. I was just convinced (somehow) qcad was using qt4. After playing a bit in qtconfig it's now palatable. IIRC it was still a lot tighter in 7.04

Thanks!
dh

I had the same problem with QCAD (installed from the repositories) and mypasswordsafe (old copy moved from my old install of ubuntu). I tried qtconfig (qt4) and it made no difference. I solved the problem by creating a **qtrc** file in the **~./qt** directory. This is a reported bug (assigned low priority when I last looked) but it is possible the routine updates have already fixed it.

My qtrc file looks like this.
```

[3.3]
libraryPath=/usr/lib/kde3/plugins/

[General]
GUIEffects=general^eanimatecombo^e
embedFonts=true
enableXft=true
font=Sans Serif,10,-1,5,50,0,0,0,0,0
fontPath=\0
useXft=true
style=Plastik

[KDE]
contrast=7
kdeAddedLibraryPaths=/usr/lib/kde3/plugins/^e

[KWinPalette]
activeBackground=#1f26ad
activeBlend=#259bb8
activeForeground=#ffffff
activeTitleBtnBg=#e6e6e6
frame=#ff0000
inactiveBackground=#cdcdcd
inactiveBlend=#ababab
inactiveForeground=#dddddd
inactiveFrame=#efebe7
inactiveTitleBtnBg=#ebebeb

[Palette]
active=#000000^e#efebe7^e#f5f3f1^e#ffffff^e#cbc1b7^e#c7c7c7^e#000000^e#ffffff^e#000000^e#ffffff^e#efebe7^e#736a60^e#f8c677^e#000000^e#0000ee^e#52188b^e
disabled=#808080^e#efebe7^e#f5f3f1^e#ffffff^e#cbc1b7^e#c7c7c7^e#c7c7c7^e#ffffff^e#808080^e#ffffff^e#efebe7^e#736a60^e#c9833b^e#000000^e#0000ee^e#52188b^e
inactive=#000000^e#efebe7^e#f5f3f1^e#ffffff^e#cbc1b7^e#c7c7c7^e#000000^e#ffffff^e#000000^e#ffffff^e#efebe7^e#736a60^e#f8c677^e#000000^e#0000ee^e#52188b^e

```

---

