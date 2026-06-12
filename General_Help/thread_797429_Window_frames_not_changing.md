---
title: "Window frames not changing"
date: 2008-05-17
forum: General Help
---

### Post by gegenki on 2008-05-17
I just installed Ubuntu 7.04 and upgraded all the way to 8.04
Then Installed my ati graphics driver
Installed Compiz-fusion
Fixed my graphics resolution.

Everything works accept the window decorator. Its there, it comes on if I set it in advanced desktop effect settings, but the only way I can change the way it looks is to goto
system>preferences>appearance
rather than using the emerald theme manager

---

### Post by macaholic on 2008-05-17
Do you have emerald installed? If not, then install it via:```
sudo apt-get install emerald emerald-themes
```

---

### Post by gegenki on 2008-05-17
Thanks
E: Package emerald-themes has no installation candidate

I've figure it out now. Emerald --replace wasn't mentioned on any of the ubuntu guides I looked up.

---

