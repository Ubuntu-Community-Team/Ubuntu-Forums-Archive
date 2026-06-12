---
title: "Conky Ubuntu 17.1 issue"
date: 2018-02-19
forum: General Help
---

### Post by jimawhitaker on 2018-02-19
I have tailored my conky to do exactly what I need except one thing. $running_processes always is zero, top and htop say different but conky is 0.  here's the full line "Processes: ${alignr}$processes ($running_processes running)"  I realize it's not a major issue just real annoying ;-)

---

### Post by stylintile on 2018-02-19
I think the problem is the command ($running_processes running) should be ($running_processes) although that still doesn't seem right on mine. it goes from 0 to 4 with firefox, geany and thunar open.

---

### Post by wildmanne39 on 2018-02-19
*Thread moved to **General Help, a more appropriate forum**.*

---

### Post by again? on 2018-02-19
Looking at some conky configs your syntax seems ok 
```
${alignr}$processes ($running_processes running)
```

Clue here might be from man conky
```
running_processes
Running processes (**not sleeping**)
```

Click on image to see a gif animation.
[[img]https://cdn.scrot.moe/images/2018/02/20/Peek-2018-02-20-09-52.md.gif[/img]](https://scrot.moe/image/65sme)

Should not be always 0 though.
If you post your whole config I can test here.

---

