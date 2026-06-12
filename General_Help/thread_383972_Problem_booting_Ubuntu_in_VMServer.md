---
title: "Problem booting Ubuntu in VMServer"
date: 2007-03-13
forum: General Help
---

### Post by UpperNinety89 on 2007-03-13
First things first, before 12:00 today I never used Linux before that extensively.

Anyway to the point. For some reason after I restarted my virtual machine with Ubuntu, the entire OS freezes and shows nothing after the initial loading screen. The orange bar fills a good 85% but then completely freaks out and just shows a blank black screen. I've tried loading different kernals, but that doesn't help at all. I have no idea where to go from here, so any help would be great.

FYI. I'm using Ubuntu 6.10

---

### Post by zvacet on 2007-03-14
ctrl+alt+F1

```
sudo dpkg-reconfigure xserver-xorg
```

---

### Post by UpperNinety89 on 2007-03-14
I tried pressing Ctrl-Alt-F1 but nothing happened.

---

### Post by zvacet on 2007-03-14
That command have to take you to terminal.it is still black but you can login.Are you telling me this is not what happened?If that is the case try ctrl+alt+backspace and see what will be.

---

