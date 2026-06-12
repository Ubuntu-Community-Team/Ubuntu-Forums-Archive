---
title: "Prevent apache2 from autostarting."
date: 2007-05-19
forum: General Help
---

### Post by loathsome on 2007-05-19
Hi'yall,

I just sat up Apache2 + PHP 5 on my Ubuntu box with no problems. Only the thing is, apache2 starts automatically on boot - I don't want this; How can I disable it?

Thanks!

---

### Post by Cene on 2007-05-19
Removing or moving off the "apache2" file from /etc/init.d/ should do the trick.

---

### Post by heimo on 2007-05-19
I wouldn't touch the start script itself, but rename this symlink:
```
sudo mv /etc/rc3.d/S91apache2 /etc/rc3.d/K91apache2
```

---

### Post by loathsome on 2007-05-19
> **heimo said:**
> I wouldn't touch the start script itself, but rename this symlink:
```
sudo mv /etc/rc3.d/S91apache2 /etc/rc3.d/K91apache2
```

Thanks for your replies!

What does that symlink do? And why wouldn't you touch the start script? (is that what's located under /etc/init.d? How does the system know that it should load up apache2?)

loathsome

---

### Post by heimo on 2007-05-19
Those symlinks are there to tell which services / scripts to run during boot. rc3.d is for runlevel 3 scripts (which is default in Ubuntu when you start) - S stands for Start and K for kill (I believe) - these symlinks point to the actual initscripts which live in /etc/init.d/ directory. You can call these scripts manually, usually with start or stop - like:
```
sudo /etc/init.d/apache2 start
```to start / stop / restart / reload services.

---

