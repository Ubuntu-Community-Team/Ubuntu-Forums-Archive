---
title: "launch a flatpak from terminal"
date: 2021-11-21
forum: General Help
---

### Post by rolfedavid on 2021-11-21
Good afternoon.
I have been trying to run a flatpak installation from the terminal:
flatpak run org.flatpak.abiword for example. This always results in an error that x86_64/master is not installed. How can I install this. I have upgraded etc all to no avail, help on this would be much appreciated.

---

### Post by Dennis N on 2021-11-21
> **rolfedavid said:**
> Good afternoon.
I have been trying to run a flatpak installation from the terminal:
flatpak run org.flatpak.abiword for example. This always results in an error that x86_64/master is not installed. How can I install this. I have upgraded etc all to no avail, help on this would be much appreciated.

I think you have the wrong Application ID for Abiword. A search finds:
```
[dmn@Sydney ~]$ flatpak search abiword
Name          Description            Application ID              Version       Branch      Remotes
AbiWord       A word processor       com.abisource.AbiWord       3.0.5         stable      flathub

```
So you should use: **flatpak run com.abisource.AbiWord**

---

### Post by rolfedavid on 2021-11-22
Thanks. So simple when you know how.

---

