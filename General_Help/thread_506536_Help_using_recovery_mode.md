---
title: "Help using recovery mode"
date: 2007-07-21
forum: General Help
---

### Post by fd9_ on 2007-07-21
I enabled "Desktop Effects"....bad idea. Now I can't use my computer because the entire system freezes when I log in. Heck, I can't even use ctrl+alt+f1 to open a terminal! I found a suggestion on another thread which said that I can disable desktop effects by removing these files:

```

rm -rf .gnome
rm -rf .gnome2
rm -rf .gconf
rm -rf .gconfd
rm -rf .metacity

```

I did this under recovery mode, but it doesn't seem to be working. Any ideas?

---

### Post by memm74 on 2007-07-25
I tried the same thing, it didn't help. I also haven't fixed the problem yet. When I enabled Desktop Effects some nVidia drivers were installed. My next try, when I go home is to compare the xorg.conf from my messe dup system with the xorg.conf from the live CD that works. Maybe it's not desktop effects themselves but some drivers that cause the problem. 

Did your system install drivers when you enabled desktop effects?

---

### Post by seebedoubleyou on 2007-07-31
i was having the same problem

type this when in recovery mode

 ```
sudo apt-get remove compiz-core desktop-effects
```

that should remove the desktop effects and you can reinstall them later if you want

---

