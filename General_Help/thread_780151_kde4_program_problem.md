---
title: "kde4 program problem"
date: 2008-05-03
forum: General Help
---

### Post by T2manner on 2008-05-03
okay. first i installed the kubuntu-desktop and got all the kde programs with it, which i wanted.
then i found out that with 8.04 i could download the kde4 desktop and get a sneak peak at it, so i did.  but now i don't want it. idk how to remove it. more importantly, i don't know how to remove the programs that it came with.. like the kopete4 the konqueror4, etc..

please help

---

### Post by Zorael on 2008-05-03
Try removing the **kubuntu-kde4-desktop** package via Adept Manager or Synaptic.

Alternatively, terminal way:
```
$ sudo aptitude purge kubuntu-kde4-desktop
```


It should get rid of all the kde4 apps, too, since that package installed them to begin with.

---

### Post by T2manner on 2008-05-03
well.
i did that, but the programs are still there, and there's still a kde4 session choice when i log in.
idk what to do, i can't even find the programs in the adept package manager

---

### Post by Zorael on 2008-05-03
```
$ sudo aptitude purge kdm-kde4
$ sudo dpkg-reconfigure kdm
```

As for the kde4 programs, you could try this. I can't guarantee it'll work, though, so at your own risk.
```
$ sudo aptitude purge ~nkde4
```

---

### Post by T2manner on 2008-05-03
thanks!
it worked great!!!
the only problem was that the "$" was messing it up.
idk why you put it there bcs with it, the command didn't work, but without it, it worked perfectly.

---

### Post by Zorael on 2008-05-03
Awesome, cheers.

The dollar-sign is syntax convention, to say that it should be entered in a terminal. Similarly, a hashmark (#) says it should be entered in a terminal with superuser permissions. As far as I know.

---

