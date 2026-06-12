---
title: "No Desktop Icons showing on GNOME"
date: 2006-10-09
forum: General Help
---

### Post by mike41 on 2006-10-09
Hello. I just recently installed Beryl and everything was working for a few days, and then all of a sudden today when I booted up the system, my desktop doesnt have any icons on it. The background is there, and my desktop folder still has all of my files, but none of them are showing on the desktop. And if i right click the desktop, I dont get any options... its not responsive.

Any help? Im no sure if this is a beryl problem or a gnome problem.

Thanks.

---

### Post by Astro96 on 2006-10-09
I have the exact same problem.  Installed beryl and a few days later, no desktop.

Running "killall nautilus" does get my desktop back, as does logging out and back in.  I'm still looking for a better fix.

---

### Post by ayoli on 2006-10-09
try run nautilus from a terminal, see output.
i had the same problem few days ago on my wife laptop, i ran nautilus from a term then saw that gnome-theme was looking for a metacity theme that doesn't exist (even if i was under beryl, the themer read the index.theme file and didn't found the metacity theme dir). i just changed it and it now works fine.

---

### Post by dentaku65 on 2006-10-09
Here is how to fix:
[http://yep.it/?suno3t](http://yep.it/?suno3t)

it is a matter of session order

---

### Post by mike41 on 2006-10-09
Thanks for all the answers. The beryl-project forums are down at the moment, but hopefully the session order thread will help me. I'll check again soon.

---

