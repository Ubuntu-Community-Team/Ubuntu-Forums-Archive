---
title: "help this nincompoop: lost password"
date: 2007-01-10
forum: General Help
---

### Post by miloske on 2007-01-10
I forgot my password and I can't log in. Is there a way to recover it or to log in without password?

---

### Post by Biggus on 2007-01-10
This may work 

[http://www.ubuntuforums.org/showthread.php?t=334778]("http://www.ubuntuforums.org/showthread.php?t=334778")

---

### Post by taurus on 2007-01-10
Boot into recovery mode from GRUB menu and at the prompt, change it to something you can remember, assuming **miloske** is your login name.

```
passwd **miloske**
```

---

### Post by miloske on 2007-01-12
Thank you taurus,

this is very easy way to reset password, so anyone who know my username (there is only one user on my pc so you don't need to know the username) can reset my password and access the system. It seems very unsafe.

---

### Post by nikhilk on 2007-01-12
I general if somesome has physical access to your machine you are not safe. But still some things can be done to improve the security. See [http://www.bastille-linux.org]("http://www.bastille-linux.org") for a good security concepts overview.

---

### Post by zetetic on 2008-04-23
> **taurus said:**
> Boot into recovery mode from GRUB menu and at the prompt, change it to something you can remember, assuming **miloske** is your login name.

```
passwd **miloske**
```

This is nuts. We shouldn't call Ubuntu a secure OS. Fortunately there are many Linux distros where you can't use this method to reset the user password.

---

### Post by CREEPING DEATH on 2008-04-24
Any time a person has physical access to your machine, it's "insecure".  If Ubuntu didn'thave this rather useful built-in feature, you could just do the same from a LiveCD.  In fact, most LiveCDs can allow unfettered access to any file on a computer.

CD

---

