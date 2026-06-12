---
title: "DVD rom/cd rw drive"
date: 2007-11-13
forum: General Help
---

### Post by alnhntr29 on 2007-11-13
I added a DVD-rom/CDrw drive after install of 7.10. Could somebody please tell me how to make the system see it? It comes up fine using the live cd, but I get nothing when I boot from hard drive. Give me a step by step if you dont mind.
Thanks in advance.

---

### Post by jfinkels on 2007-11-13
Does it show up when you do ```
sudo lshw
```? (You may need to pipe the output through 'less':```
sudo lshw|less
```).

---

### Post by alnhntr29 on 2007-11-13
Does not show up at all using that code from terminal. Off topic from what I posted, I am running a celeron 2.5 ghz. It is showing That the size is 2533 mhz which is correct. It shows the max at 3600 mhz which I assume it could be overclocked to. But it shows the actual clock speed at 533 mhz. Is that right? Anyways, thats something I saw when i ran that code.
It is not showing my drive at all.

---

