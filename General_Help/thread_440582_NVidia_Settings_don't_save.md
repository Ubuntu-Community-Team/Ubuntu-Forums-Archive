---
title: "NVidia Settings don't save"
date: 2007-05-11
forum: General Help
---

### Post by AEngineer on 2007-05-11
I used wubi to install Feisty on my XP machine.  All worked well once I reallized how much space it required.

I then used Automatix2 to install NVidia drivers for my machine (a pair of Dell 19" screens).

I can set up the screens (twin mode) and work very happily using the "NVidia Settings" application.  It appears to save the settings, but when I restart Ubuntu I'm back to a single screen and have to repeat the whole procedure.  I'm not clear if this is a wubi or a Ubuntu problem, but it's annoying.

Any suggestions?

Jim Mitchell

---

### Post by sdlynx on 2009-06-24
have u tried running the nVidia settings application under root?  for some reason I was having a problem like that and running as root fixed it...

---

### Post by merlinus on 2009-06-24
```

gksu nvidia-settings

```

---

