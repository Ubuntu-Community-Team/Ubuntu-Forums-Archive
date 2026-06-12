---
title: "loe and behold, Switfox is missing from Automatix2"
date: 2006-12-12
forum: General Help
---

### Post by linuxted on 2006-12-12
I've installed Swiftfox with Automatix2 a month ago. After an update to Automatix2 I don't see Swiftfox listed as an installed option in any of the Automatix2 folders.

Any ideas?  Do you see the same thing?

Thanks

---

### Post by pay on 2006-12-12
You can install it  by :```
sudo nano /etc/apt/sources.list
```and then add these lines at the bottom```
deb http://getswiftfox.com/builds/debian unstable non-free
```and then update ```
sudo aptitude update
```and then install it with ```
sudo aptitude install <package>
```where the package is one of these ```
swiftfox-athlon
swiftfox-athlon-xp
swiftfox-athlon64
swiftfox-k6-2
swiftfox-pentium-m
swiftfox-pentium2
swiftfox-pentium3
swiftfox-pentium3m
swiftfox-pentium4
swiftfox-prescott
```

---

