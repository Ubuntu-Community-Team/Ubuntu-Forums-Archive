---
title: "Failed to start session on login screen"
date: 2017-10-06
forum: General Help
---

### Post by chris336 on 2017-10-06
After installing, uninstalling, and reinstalling various software on my system I restarted my computer. When attempting to login I receive a "Failed to start session" error. After some searching I tried using the TTY to install the Ubuntu desktop, but am receiving this error: "The following packages have unmet dependencies: <a list of dependencies> E: Unable to correct problems, you have held broken packages." I was receiving a similar error which is why I initially restarted. Any advice is appreciated.

---

### Post by efflandt on 2017-10-07
What did you install, uninstall, and reinstall? And what is the list of missing dependencies? Impossible for anyone to help you much without knowing what you did (and Ubuntu version).

From a terminal you might try to fix broken/missing packages with:```
sudo apt install -f
```Blindly carefully enter your normal user password when sudo requests it (nothing echoed to screen). If using an Ubuntu version older than 16.04 use **apt-get** instead of **apt**.

---

