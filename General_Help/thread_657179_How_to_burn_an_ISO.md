---
title: "How to burn an ISO?"
date: 2008-01-03
forum: General Help
---

### Post by Zdravko on 2008-01-03
Hey!
I have an iso file. How do I burn it to a CD? Or better - a DVD?

---

### Post by -Zeus- on 2008-01-03
for a CD, right click on the file and click "write file to CD"

---

### Post by tech9 on 2008-01-03
you should be able to right-click and write to disk...
it's that simple
Ubuntu knows that it's an ISO and will burn it as one.

---

### Post by Zdravko on 2008-01-03
Mmmh! Great! I will give it a try!

---

### Post by fjgaude on 2008-01-03
Right clicking on the file expands the ISO file to disk and then you are asked for your CD or DVD. Then it writes. Works well.

---

### Post by ~LoKe on 2008-01-03
CLI:
> growisofs -dvd-compat -Z /dev/**scd0**=**/path/to/dvd.iso**
Replace scd0 with your device, and change the path to your...path.

---

