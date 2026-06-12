---
title: "Page scrolling is not smooth on Xubuntu"
date: 2020-05-08
forum: General Help
---

### Post by peter1897 on 2020-05-08
I have laptop Lenovo Thinkpad T420 with dual boot - Xubuntu 20.04 and Windows 7. On Xubuntu page scrolling in Firefox, and other browsers, is not as smooth as it on Windows 7. Why is that? Is this video driver issue or something else. My video card is Intel HD Graphics 3000.

---

### Post by CelticWarrior on 2020-05-08
> Is this video driver issue or something else. My video card is Intel HD Graphics 3000. 				

It shouldn't be but probably is.
A couple of years ago I've read something about Intel dropping support for some legacy graphics hardware in Linux and it was about the exact same graphics you have in a Gigabyte miniPC or something like that.

Windows 10 may or may not have a similar problem if it's now running the Microsoft Basic driver instead of Intel's. The old driver in Windows 7 works but you shouldn't use Windows 7 connected to the internet under no circumstance. It has no security updates since 2014 and is, in a nutshell, a sitting duck for all sorts of attacks.

---

### Post by peter1897 on 2020-05-08
So, there is no fix?

---

### Post by CelticWarrior on 2020-05-08
I'm afraid there is no fix.

---

### Post by VMC on 2020-05-08
See if Compositor is on. WindowManagerTweaks>Compositor. It should already be active.

---

### Post by peter1897 on 2020-05-08
> **VMC said:**
> See if Compositor is on. WindowManagerTweaks>Compositor. It should already be active.

Yes, it's on.

---

### Post by peter1897 on 2020-05-08
How to view which video driver i have installed?

---

