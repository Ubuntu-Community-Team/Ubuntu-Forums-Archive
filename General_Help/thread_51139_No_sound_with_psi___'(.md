---
title: "No sound with psi   :'("
date: 2005-07-22
forum: General Help
---

### Post by szdavid on 2005-07-22
Hello

I am using PSI 0.9.3 on Ubuntu Hoary ; play is installed but it doesnt work...
When I write ```
play /usr/local/share/psi/sound/chat1.wav
```


it prints > playing /usr/local/share/psi/sound/chat1.wav

but no sound is played

what could I do ? ?

Thanks

---

### Post by tommi on 2005-08-02
if u use ubuntu and esd is ur soundserver dont use play, use esdplay.
if u use kubuntu and arts is ur soundserver dont use play, use artsplay.

if u have not installed these programs (are not installed in standard-install) u have to apt-get it ..

---

### Post by nekr0z on 2006-06-15
Much easier:
> sudo apt-get install sox
and "play" works flawlessly.

---

