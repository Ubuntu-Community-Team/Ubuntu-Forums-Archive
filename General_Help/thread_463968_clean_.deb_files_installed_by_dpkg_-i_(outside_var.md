---
title: "clean .deb files installed by dpkg -i (outside /var/cache/apt/archives)"
date: 2007-06-04
forum: General Help
---

### Post by macubo on 2007-06-04
Hi all, i finally got my laptop running feisty 64bit and set wireless&wpa up.
Now I'm going to remove some junk from my Desktop. In particular I downloaded and installed by dpkg -i the .deb files of the ATI driver. These files are placed in my Desktop and are locked. This prevents me (as normal user) from deleting them.

I'm not sure that apt-clean may work outside the var/cache/apt/archives folder, and I don't want to brake something by simply deleting them as superuser.

Thankyou

---

### Post by taurus on 2007-06-04
After you install them, you don't need those .deb files anymore so it's safe to remove them from your ~/Desktop.

```
gksudo nautilus
```

---

### Post by macubo on 2007-06-04
ok then thank you

---

