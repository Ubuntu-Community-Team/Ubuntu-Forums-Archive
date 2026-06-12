---
title: "Some keyboard letters and space not working on laptop"
date: 2020-09-19
forum: General Help
---

### Post by arska79 on 2020-09-19
Hello,
I am totally new ubuntu user, just installed ilatest version on my lenovo laptop succesfully but I encountered very strange problem. On laptop\s keyboard b, n and space are not working at all. What is most strange it worked at some point, but mysteriously these letters and space were disabled and I did not find any solutions on region and language settings although I tried to change language settings several times. How on earth it is possible this kind of error happen and how to solve it. I am writing this msg on external keyboard which is working impeccably. Naturally I rebooted laptop several times but problem did not solve.
Arska

---

### Post by CelticWarrior on 2020-09-19
Welcome.

Please contact tech support. It's an hardware issue.

---

### Post by HermanAB on 2020-09-19
Howdy,

This is an ancient bug in X11/Xorg.  Sometimes, it forgets a key or three.  This happened to me about 20 years ago.

The solution that I used, was to run *xev* to see the key codes and then use *xmodmap* to reset the offending keys to themselves.

Some googling on xmodmap will get you going.  There should be some examples in these forums also.

---

### Post by Impavidus on 2020-09-20
Either a hardware issue or a weird bug (BTW, I never heard of that bug before). First try the second solution. If xev doesn't give you any keycodes on those keys, use the first solution.

---

