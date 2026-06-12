---
title: "Ram"
date: 2008-05-13
forum: General Help
---

### Post by Blakefreak on 2008-05-13
I read in another thread that I can use more of my RAM to cache frequently used or previously opened programs.
But unfortunately I did not see the command that allows me to change this option.
I have three gigs of ram and usually only use about ten percent... twenty if I'm running a game and a few other apps.
Any suggestions?

---

### Post by sdennie on 2008-05-13
That functionality happens automatically without any user interaction.  To see exactly how it's working, open a terminal and type:

```

free -m

```

---

### Post by pointone on 2008-05-13
You were most likely reading about [preload]("http://sourceforge.net/projects/preload").

```
sudo apt-get install preload
man preload
```

---

