---
title: "Few beginner questions"
date: 2007-05-07
forum: General Help
---

### Post by KillMeh on 2007-05-07
Hello, started to use Kubuntu yesterday, kinda nice distro. :)

1) How to change default runlevel and number of virtual consoles (tty1, tty2 and etc, dont know how this is called in english)? /etc/inittab doesn't exists.
2) About adept (nice program, better than synaptic imho). When something is being installed/removed, you can press details - then console appears. But in center of that console you can see numbers (they show console's size), how to remove them? Here's screenshot: [http://img209.imageshack.us/img209/4269/snapshot1ai1.png](http://img209.imageshack.us/img209/4269/snapshot1ai1.png) This is getting on my nerves ;/
3) Kernel optimised for k7. Installed linux-headers-k7, linux-image-k7, linux-k7, but in GRUB i can choose only generic kernel and no k7 kernel in /boot ;/ With Debian that worked fine..

Thats' all. For now.

---

### Post by mexlinux on 2007-05-07
> **KillMeh said:**
> Hello, started to use Kubuntu yesterday, kinda nice distro. :)
Reply With Quote
2) About adept (nice program, better than synaptic imho). When something is being installed/removed, you can press details - then console appears. But in center of that console you can see numbers (they show console's size), how to remove them? Here's screenshot: [http://img209.imageshack.us/img209/4269/snapshot1ai1.png](http://img209.imageshack.us/img209/4269/snapshot1ai1.png) This is getting on my nerves ;/


(yes it is) the console size is a konsole preference, since adept runs as root open konsole as root and disabble that option:
```

kdesu konsole

```
```

Menu>Preferences>Configure>General Tab>Show Window Size o Resize

```
Mine is in spanish so names should be different

---

### Post by KillMeh on 2007-05-07
> **mexlinux said:**
> (yes it is) the console size is a konsole preference, since adept runs as root open konsole as root and disabble that option:
```

kdesu konsole

```
```

Menu>Preferences>Configure>General Tab>Show Window Size o Resize

```
Mine is in spanish so names should be different
Thanks. :)

How about runlevels?

---

