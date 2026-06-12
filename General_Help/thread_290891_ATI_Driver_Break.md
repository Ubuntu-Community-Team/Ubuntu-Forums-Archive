---
title: "ATI Driver Break"
date: 2006-11-01
forum: General Help
---

### Post by calvinthomas on 2006-11-01
Hi guys, being really stupid earlier I went into overdrive trying to up my screen resolution in KDE, I did it by dpkg reconfigure-xserver-xorg.

Now when I went back in my drivers had messed up, I didn't worry I thought i'll just reinstall them, I then decided to try the latest drivers 8.30.3 using the wiki, it seemes to be going ok until I got to the final two lines i.e. the ones containing:

```
sudo aticonfig
```

When I try either of those lines it says: ```
sudo: aticonfig command not found
```

So then I thought I'll just try restoring my old xorg file, so I did that and now my drivers are installed correctly (fglrxinfo gives the right information) and Beryl and XGL work and I get no black borders with Kiba-Dock but.... It is unusably slow!

How can I fix this?

Calv

---

### Post by calvinthomas on 2006-11-02
bump, I really need to get this sorted, anyone have any idea how I can get the command:

```
sudo aticonfig --initial
``` to work? I'm sure that would sort it.


Note: I get this when trying some stuff, which seems to be the problem:

```
calvin@Calvin:~$ sudo aticonfig --initial
Password:
sudo: aticonfig: command not found
calvin@Calvin:~$ aticonfig
bash: /usr/bin/aticonfig: Permission denied
calvin@Calvin:~$ sudo su
root@Calvin:/home/calvin# cd
root@Calvin:~# aticonfig
bash: /usr/bin/aticonfig: Permission denied
root@Calvin:~#
``` 


Calv

---

### Post by calvinthomas on 2006-11-02
Problem solved, here was my solution, very easy really.

Opened up konqueror with root priviledges by:

```
kdesu konqueror
```

Navigated to /usr/bin

Found the ati config file, went to properties, permissions and noticed executable wasn't checked, checked that, re-did the wiki and everything is perfect!

Calv

---

### Post by calvinthomas on 2006-11-02
Problem solved, here was my solution, very easy really.

Opened up konqueror with root priviledges by:

```
kdesu konqueror
```

Navigated to /usr/bin

Found the ati config file, went to properties, permissions and noticed executable wasn't checked, checked that, re-did the wiki and everything is perfect!

Calv

---

