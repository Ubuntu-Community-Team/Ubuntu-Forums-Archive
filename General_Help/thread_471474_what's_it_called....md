---
title: "what's it called..."
date: 2007-06-12
forum: General Help
---

### Post by hoozey on 2007-06-12
is there some sort of a console type thing that will display things i do in the gui? i mean, so if i right clicked on a hard drive and clicked mount, it would say "mount hda1 blah blah" or whatever? If so, what's it called or how do i get it?

thanks

---

### Post by airblade on 2007-06-15
You may check the /var/log/, and use
```
tail -f FILE
```

Example:
```
tail -f /var/log/dmesg
```

I'm not sure what your intentions are, but i hope this helps.

---

