---
title: "[SOLVED] cross dependency - cant install two .debs!?"
date: 2007-09-22
forum: General Help
---

### Post by Kenobi on 2007-09-22
Hi,

I'm stuck with some SIMPLE installations. For example I want to install LBreakout, which consists of two packages (lbreakout2, lbreakout2-data). But whenever I try to install one .deb - file it says that it has a dependency and can't install without the other, and it wants to download it (what it can't cause there is no internet). Normally, dependencies are only one way round, but this time they need EACH OTHER!

How can I persuade the computer to install both packages at once, or to, simply, get the dependency from the same folder?

---

### Post by aidanr on 2007-09-22
I think if you do it from the terminal it should work:

```
cd /path/to/saved/debs
sudo dpkg -i *.deb
```

---

### Post by Kenobi on 2007-09-22
Thank you aidanr!! 

You gave me the perfect solution! If I put this line in a file I can use it as a general install file for everything!!

All right.... we should also give a notice to the ubuntu developers that their crazy .deb-installer should check the same directory by default.

---

