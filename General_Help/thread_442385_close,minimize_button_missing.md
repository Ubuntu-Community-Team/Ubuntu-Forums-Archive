---
title: "close,minimize button missing"
date: 2007-05-13
forum: General Help
---

### Post by coffee-n-cream on 2007-05-13
hello there i got this problem recently.my close and minimize button seem to have disappear completely from all programs.basically the 3 common buttons @ the top right of every program.how do i make it reappear again? i didnt do anything (as far as i know) to make the buttons disappear.pls help! thx alot

---

### Post by mills on 2007-05-13
this is the only solution i found for ya

```
sudo aptitude purge ubuntu-desktop && sudo aptitude clean && sudo aptitude update && sudo aptitude install ubuntu-desktop && sudo /etc/init.d/gdm restart

```

[http://ubuntuforums.org/showthread.php?t=415244&highlight=missing+buttons](http://ubuntuforums.org/showthread.php?t=415244&highlight=missing+buttons)

searched for missing buttons;)

hope it works

---

### Post by dpar on 2007-05-13
If your running Beryl it will do that. See this post-    [http://ubuntuforums.org/showthread.php?t=431598&highlight=close+buttons+beryl](http://ubuntuforums.org/showthread.php?t=431598&highlight=close+buttons+beryl)

---

### Post by digish778 on 2008-05-30
Thank you mills

---

