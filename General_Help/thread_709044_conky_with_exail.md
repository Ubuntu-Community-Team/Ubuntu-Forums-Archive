---
title: "conky with exail?"
date: 2008-02-27
forum: General Help
---

### Post by uberlube on 2008-02-27
Hi everyone! I switched over from KDE to XFCE on my desktop and Im just trying to get all my customizations done, and now I'm working with conky. Im trying to get conky to pull info from Exail and so far Ive got it to show the song name and artist but I want it to show a status bar, just like I did with Amarok in KDE. Heres what I have in there, but the last line  doesnt work. Is this a status bar or something entirely different? Do I have to have a mySQL file in my home folder like Amarok, or is there a simpler way to do it?

```
${color green}Exaile ${hr 1}$color

${alignc}${color red} ${execi 10 exaile --get-title} 
${alignc}${color red} ${execi 10 exaile --get-artist} 
${alignc}${color red} ${execi 10 exaile --get-status}
```

---

### Post by uberlube on 2008-02-27
Bump:-\"

---

### Post by uberlube on 2008-02-27
Bumpity, bump, bump

---

