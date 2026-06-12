---
title: "Quick question"
date: 2008-05-10
forum: General Help
---

### Post by Cookie1456 on 2008-05-10
I had Ubuntu installed on another computer, it got messed up (board died) so I used the hard drive from that computer and put it in my computer with Windows XP, reformatted it, and so I have the drives C: and G:. I installed it on G, my windows XP is on C:. When I boot up I have to edit the grub boot line to hd(1,0) each time to boot Ubuntu, is there anyway to permanently change this. I never messed with boot stuff.

Wubi is a great program none the less, was extremely simple to install.

---

### Post by CAsurfer on 2008-05-10
I haven't used Wubi, but with a regular install, this problem would be fixed by editing /boot/grub/menu.lst. Make sure you make a backup first!

---

