---
title: "How to refresh the icon theme cache ?"
date: 2013-10-21
forum: General Help
---

### Post by hizo on 2013-10-21
Hi,

I would like change and refresh the icon theme of Kubuntu (kde) in command lines.
 
I change the icon theme configuration in kdeglobals file:
```
[Icons]
Theme=oxygen
```

But I can not reload the cache...

I tested :
```
sudo touch "/usr/share/icons/hicolor"
touch "${HOME}/.kde/share/icons"

kbuildsycoca
kbuildsycoca --noincremental

kquitapp plasma-desktop
plasma-desktop

rm /var/tmp/kdecache-hizoka/icon-cache.kcache

```

But not refresh icons...


What is the command line who is use by ksystem when we change the theme ?!


Thank you !

---

