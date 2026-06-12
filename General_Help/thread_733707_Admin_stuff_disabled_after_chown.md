---
title: "Admin stuff disabled after chown"
date: 2008-03-24
forum: General Help
---

### Post by Angadude on 2008-03-24
Hey I'm a jackass.

So I su root
and chown '/' to my own user...

and now i cant open the synaptic, users n groups, etc! :(

Please help!

---

### Post by dcstar on 2008-03-24
> **Angadude said:**
> Hey I'm a jackass.

So I su root
and chown '/' to my own user...

and now i cant open the synaptic, users n groups, etc! :(

Please help!

```
sudo chown root /
```

---

### Post by Angadude on 2008-03-24
synaptic n others still dont open! plspls helP!

---

### Post by pointone on 2008-03-24
If you chowned / recursively (i.e., "chown username / -R", then you have a serious problem. There are a number of files that need to have their permissions set "just-so". The reverse operation would then be to recursively chown as root, but this isn't a perfect fix. CUPS, for example, requires ownership of certain files by "cupsys/lpadmin", for example.

Also, if you chowned both user and group, then you'll need to reset both back to root.

The only way to recover fully from this that I know of is a reinstall. Posting the exact error message you receive will help us repair your install as best we can, though.

---

