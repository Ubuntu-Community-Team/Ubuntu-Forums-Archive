---
title: "Problems with Libre Office on Ubuntu 24.04"
date: 2024-08-21
forum: General Help
---

### Post by apgp on 2024-08-21
When I open Libre Office this message appears and after a short time it freezes and I have to restart it:
Warning: failed to launch javaldx - java may not function correctly. 
I don't know how to solve it. Help is appreciated. Thank you.

---

### Post by #&amp;thj^% on 2024-08-21
Can you show us this:
```
firejail --ignore=apparmor /usr/bin/libreoffice

```
Also libreoffice is available as flatpak as well

---

### Post by #&amp;thj^% on 2024-08-21
To fix the java warning install these:
```
sudo apt install default-jre libreoffice-java-common

```

As for your freezing look in "dmesg"
maybe this would be useful:
```
sudo dmesg --follow-new --human | grep apparmor | grep libreoffice 

```
Open "libreoffice" untill it freezes and paste back that return.

Anyway I'm not sure I'll be around much longer so good luck to you.

---

### Post by Impavidus on 2024-08-22
Libreoffice works fine without Java. It's optional and not installed by default. Don't install Java unless you really need it. The Java warning is unrelated to the freezes.

---

