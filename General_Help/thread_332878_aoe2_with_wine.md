---
title: "aoe2 with wine?"
date: 2007-01-06
forum: General Help
---

### Post by mkent91 on 2007-01-06
How do i run AOE2 using wine? i have the cd. can come guide me thru it?

---

### Post by Hossie on 2007-01-06
You can just wine AoESetup.exe, but in my experience the game does not work well. You have to run it with a high priority (nice -19 ...) but still its very slow. And for me, AoE only ran in 640x480 and changed the X11 resolution permanently, so I always had to kill X11 afterwards. But it should run fine, though. Afaik you also need a no-CD patch.

---

### Post by mkent91 on 2007-01-06
so i prolly shouldnt even try haha.... how about HITMAN 2? does that work and how would i install it..?

---

### Post by mkent91 on 2007-01-06
how do i wine something? its confusing for a person who knows nothing = ME!

---

### Post by Hossie on 2007-01-06
First, mount your cdrom (just insert it and select "open in new window"), then open a new terminal (under "System"), cd to /media/cdrom0 (or cdrom1), and type

```
wine myexe.exe
```

---

