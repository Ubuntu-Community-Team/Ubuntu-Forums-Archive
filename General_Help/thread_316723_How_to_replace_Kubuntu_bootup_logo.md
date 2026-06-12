---
title: "How to replace Kubuntu bootup logo"
date: 2006-12-11
forum: General Help
---

### Post by ghepardo on 2006-12-11
Hi, I have ubuntu 6.10 installed. I installed and then remove kubuntu-desktop via apt-get, but this operation changed my logo start from the ubuntu one to the kubunto one. How do I restore the ubuntu logo!?

p.s. the kubuntu destktop was completely and correctly removed, only this things remained.

---

### Post by taurus on 2006-12-11
Are you talking about the gdm?

```
sudo aptitude update
sudo aptitude install gdm
sudo /etc/init.d/gdm start
```

---

### Post by lumpki on 2006-12-11
I think gdm is probably already installed. To switch from the KDE login to the Gnome one, do
```
sudo dpkg-reconfigure gdm
```
(or sudo dpkg-reconfigure kdm) and select gdm for Gnome, or kdm for KDE. The login managers kdm and gdm are interchangable, you can use either one with either desktop.

---

### Post by ghepardo on 2006-12-12
tnx.

---

