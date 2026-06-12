---
title: "no console with vanilla kernel"
date: 2006-08-28
forum: General Help
---

### Post by rohrbold on 2006-08-28
Hello friends,

recently I had to compile a vanilla kernel (2.6.17.11) for some testing purposes. I did that using "make oldconfig" to create a .config file, built the kernel image via 
```
sudo make-kpkg --initrd --revision i686mr binary
```
and installed it. The kernel works fine so far except that I don't get any boot messages to see (only an empty black screen) nor can I switch to one of the consoles. If I like to do so (via Ctrl+Alt+F1), I just get some dizzy noise on my screen. I need the console urgently for this testing fascility but I have no idea what might fix this issue.
Does anybody know what I can do?

Martin

---

