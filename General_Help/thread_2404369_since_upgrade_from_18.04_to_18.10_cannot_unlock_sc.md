---
title: "since upgrade from 18.04 to 18.10 cannot unlock screen anymore"
date: 2018-10-23
forum: General Help
---

### Post by magowiz82 on 2018-10-23
Hi,
I recently updated from ubuntu 18.04 to 18.10 and every time I lock the screen I cannot unlock it anymore, the only thing I can do is to go on another virtual terminal and launch reboot (even restarting gdm3 service doesn't work), when I see the shield I cannot access to password input, dragging with mouse or pressing enter doesn't work.
I'm almost certain that is a gdm issue since I tried also lubuntu flavour and I didn't have any issue.

Do you have any hint to what to try to understand what happens and, hopefully solve it ?
Thanks in advance.

magowiz

---

### Post by dino99 on 2018-10-23
After each dist-upgrade, think to clean the system with: autoremove, gtkorphan & bleachbit (as root, select carefully settings)

---

### Post by magowiz82 on 2018-10-23
ok I will try these. Anyway, just to give further information : Also with ligthdm there are no issues.

@dino99: with autoremove you mean : apt-get autoremove ?

---

### Post by manodg on 2018-11-04
Are you using gnome extensions? 

I had the exact same problem and solved it by disabling all extensions. I'm not sure which extension was causing the problem, but it solved the issue.

---

### Post by magowiz82 on 2018-11-04
Yes,I forgot to report back: also in my case was an extension causing tue issue, probably time++.

---

