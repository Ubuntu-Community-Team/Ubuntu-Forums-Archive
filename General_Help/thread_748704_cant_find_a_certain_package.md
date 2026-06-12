---
title: "cant find a certain package"
date: 2008-04-07
forum: General Help
---

### Post by hart02 on 2008-04-07
where can i find a package called linux-restricted-modules-2.6.22-14-cell? I need it to run restricted  drivers manager on my ppc machine.

---

### Post by sekinto on 2008-04-07
Do you have all the repositories enabled?

System>Administration>Software Sources

I recomend checking everything except for the CD-ROM (if you already have an internet connection). After you have the sources checked you will have to exit that and open up a terminal and type "sudo aptitude update".

Then try using Restricted Drivers Manager again. If it still isn't working look for the package using Synaptic Package Manager. You can hit the search button and type in "linux-restricted-modules" and look for it.

---

