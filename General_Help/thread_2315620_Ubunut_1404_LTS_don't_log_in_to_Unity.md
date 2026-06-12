---
title: "Ubunut 14:04 LTS don't log in to Unity"
date: 2016-03-01
forum: General Help
---

### Post by Azyx on 2016-03-01
After uppgrade and reboot, Ubuntu don't log in to Unity. A cli-promt to log in, but my keyborad don't work. I can connect true ssh and run from there. I suspect problem with the proretarian ATI-driver, that are now quite old(Catalyst 14.x) installed. I can no use the keybord (test with diffent working keyboard), but i can access thrue SSH. Any advice to se the error from ssh terminal?

Cheers

Edit: Additional info. .Xauthority in my home-folder had chaged to be owned by root root, and not by me. That had happens before when I have chanded gfx-card on other computers, and I have been able to log in, but it did not help here.

Solved: Remove fglrx-drivers and i worked
```
 sudo apt-get purge fglrx* 
```

---

