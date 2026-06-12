---
title: "[SOLVED] resolvconf fails at boot"
date: 2008-01-19
forum: General Help
---

### Post by y-lee on 2008-01-19
About a week ago Ubuntu starting saying setting up **resolvconf … [fail]** or something like that during boot. It doesn’t seem to hurt anything tho the software i regularly use still works. According to Synaptic Package manager I don’t have resolvconf installed, unless i installed it some other way but I don’t recall doing so … not that that means much. lol


Don’t know if this will help but here’s more detail about the error:
```

setting up resolvconf....
run-parts: /etc/resolvconf/update.d/libc exited with return code 1
```

I doubt it matters but the error showed up the same day and after I compiled *Pidgin 2.3.1.* No problems with the compilation tho or the program so I think it is just a coincidence.

Any ideas?

---

### Post by y-lee on 2008-01-20
I installed resolvconf and now no longer get the message. Have no idea why it was starting up and failing but not showing up as installed. No idea why i need it either but no error message and so far things seem to work.

---

