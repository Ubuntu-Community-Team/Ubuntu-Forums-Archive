---
title: "can no loger log into wayland session after gnome update"
date: 2017-10-27
forum: General Help
---

### Post by monkeybrain20122 on 2017-10-27
I can no longer log into wayland. The screen freezes for a long time and then drops back to the GDM login screen. Gnome-xorg still works.
Since I don't use wayland normally I am not sure when did it happen (It used to work in new install and still worked after installing unity) It may be due to update today.

```
Upgraded the following packages:
gir1.2-mutter-1 (3.26.1-2ubuntu1) to 3.26.1-2ubuntu2
gnome-shell (3.26.1-0ubuntu4) to 3.26.1-0ubuntu5
gnome-shell-common (3.26.1-0ubuntu4) to 3.26.1-0ubuntu5
libmutter-1-0 (3.26.1-2ubuntu1) to 3.26.1-2ubuntu2
mutter (3.26.1-2ubuntu1) to 3.26.1-2ubuntu2
mutter-common (3.26.1-2ubuntu1) to 3.26.1-2ubuntu2

```

Ubuntu 17.10.

---

### Post by monkeybrain20122 on 2017-10-29
Did a fresh install and fully upgrade and it works again. Probably some corrupt settings..

---

### Post by monkeybrain20122 on 2017-10-30
OK. the culprit turns out to be the Easyscreencast extension. Enable it then cannot log into Wayland, Disable it then it works again.

---

### Post by irv on 2018-02-07
I found the same problem. How did you Disable it? I had to boot with the live USB go into ```
 /home/.local/share/gnome-shell/extensions/ 
``` change the read-only rights and delete the entire directory for EasyScreenCast.

---

### Post by irv on 2018-02-08
See post #12 in [https://ubuntuforums.org/showthread.php?t=2384134&page=2]("https://ubuntuforums.org/showthread.php?t=2384134&page=2")

---

