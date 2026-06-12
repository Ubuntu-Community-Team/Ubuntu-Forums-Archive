---
title: "need help editing sysvinit"
date: 2007-01-28
forum: General Help
---

### Post by enix on 2007-01-28
i need help editing my sysvinit file so that i can get conky to load as the last item. I cant seem to find any info after googling my eyes out (maybe i just dont know what to look for).



thanks in advance.

---

### Post by kerry_s on 2007-01-28
Use a script, in your home folder make a text file, name it .conky, inside put

#!/bin/sh
sleep 5
conky &

make it executable(chmod +x .conky)

Put the path in your session startup(/home/you/.conky)

sleep 5 makes it wait 5 seconds before starting, adjust it according to what you need.

---

### Post by enix on 2007-02-04
thank you so very much!

---

