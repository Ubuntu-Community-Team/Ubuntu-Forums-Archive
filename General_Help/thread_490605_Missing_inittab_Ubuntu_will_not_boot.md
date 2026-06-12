---
title: "Missing inittab Ubuntu will not boot"
date: 2007-07-02
forum: General Help
---

### Post by ComposerDude on 2007-07-02
Hello.
I recently updated some software, and then rebooted. This is the error I received:

```
/etc/inittab[1]: missing id field
/etc/inittab[2]: missing process field
```

Ubuntu will not even boot into recovery mode.

If anyone can help it would be greatly apreciated.

Currently I am going to try and replace inittab manually through the 7.04 Live CD and try rebooting. My guess is that it's the wrong way to do it, and that it may not work.

Hey, I simply re-installed ubuntu. KDM had been giving me configuration problems before the crash, so I just gave up and started fresh. Thanks.

---

### Post by Jasper84 on 2007-07-18
I just read Ubuntu uses upstart:
[http://upstart.ubuntu.com/](http://upstart.ubuntu.com/) read it here: [http://ubuntuforums.org/showthread.php?t=292507](http://ubuntuforums.org/showthread.php?t=292507)
So prolly replacing  inittab wont work. Perhaps the solution is somewhere after a forum search for inittab, or in the links.

---

