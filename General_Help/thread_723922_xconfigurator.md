---
title: "xconfigurator"
date: 2008-03-14
forum: General Help
---

### Post by hirohitosan on 2008-03-14
Hello there. I installed kubuntu on one of my computer and the screen goes blank and I cannot see nothing. I think my video card cannot support the monitor resolution or something like that. How can I set up the screen resolution from a console.

I already tried
Ctrl+Alt+F2
```
sudo xorgconfig
sudo: xorgconfig: command not found
```
there are some console tools for tweaking X server?

Thanks

---

### Post by kesman on 2008-03-14
the command is
```

sudo dpkg-reconfigure xserver-xorg

```

---

