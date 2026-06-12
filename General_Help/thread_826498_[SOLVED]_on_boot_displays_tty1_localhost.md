---
title: "[SOLVED] on boot displays tty1 localhost"
date: 2008-06-11
forum: General Help
---

### Post by omega17 on 2008-06-11
I want to boot in to Ubuntu 8.04 and when I do i get:

```
Ubuntu 8.04 localhost tty1
Localhost login:
```
I just want to boot can I get past this?
Runing 8.04 Just installed

---

### Post by iaculallad on 2008-06-11
> **omega17 said:**
> I want to boot in to Ubuntu 8.04 and when I do i get:

```
Ubuntu 8.04 localhost tty1
Localhost login:
```
I just want to boot can I get past this?
Runing 8.04 Just installed

Input your login name and password. Issue the command startx to get you to your GUI

```
startx
```

---

### Post by molotov00 on 2008-06-11
Did you install the server version? If you did, and you want a GUI, then you need to install one:

sudo apt-get install ubuntu-desktop

The GUI should start automatically. startx is the command to manually "Start X". The desktops in Linux are run by an "X Server", fyi.

---

### Post by omega17 on 2008-06-11
i installed the desktop version

---

### Post by molotov00 on 2008-06-12
> **omega17 said:**
> i installed the desktop version

Did you get it working with startx then?

---

### Post by omega17 on 2008-06-12
> **molotov00 said:**
> Did you get it working with startx then?

no grub said that no OS was installed so i am re-installing

---

### Post by omega17 on 2008-06-12
when i login under my username:computer and my password it says invalid, and root lets me in but 'startx' is invalid

---

### Post by omega17 on 2008-06-12
fixed.

---

