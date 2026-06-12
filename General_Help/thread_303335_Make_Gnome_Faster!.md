---
title: "Make Gnome Faster!"
date: 2006-11-20
forum: General Help
---

### Post by davebradford on 2006-11-20
I've posted about this before, but no luck, few months down the line and it's really getting too me so i thought i'd do one last shout out and see if anything new comes up!

I'm running ubuntu on an older laptop, Celeron 1.3Ghz, 256MB RAM, 40 Hard Disk, Onboard graphics S3. And i'm finding it hard using gnome without it being very very very very slow! I really love gnome, and i hope i don't have to move to fluxbox, so if anybody knows hacks, to improve the way gnome works then i'm all ears! 

Thanks again!

---

### Post by frodon on 2006-11-20
This thread contain useful informations and might help you : [http://ubuntuforums.org/showthread.php?t=214300](http://ubuntuforums.org/showthread.php?t=214300)

At the time when i didn't have a powerful computer i used xfwm4 (the XFCE WM) instead of metacity and it increased a bit the performances and saved me much RAM.

Good luck

---

### Post by yopnono on 2006-11-20
Add this to the grub kernel option ```
elevator=cfq
```

[https://wiki.ubuntu.com/CFQbyDefault](https://wiki.ubuntu.com/CFQbyDefault)

---

