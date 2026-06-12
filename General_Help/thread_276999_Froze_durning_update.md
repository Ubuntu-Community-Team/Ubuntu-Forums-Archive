---
title: "Froze durning update"
date: 2006-10-13
forum: General Help
---

### Post by MacUsr on 2006-10-13
I was updating Ubuntu and it froze. But it was updating something important I think. I now get a kernel panic at startup :( I waited a minute and nothing happened, I restarted again and got a kernel panic, and a few more lines of something. I restarted again and got the same kernel panic at the first time Is there a way I can fix this without a reinstall?

---

### Post by swordsman on 2006-10-13
if you were indeed updating your kernel, you should still be able to go back to the previous kernel and use that instead.

hit esc when you see the grub menu, and choose a kernel with a lower version number and then run apt-get dist-upgrade again.

---

