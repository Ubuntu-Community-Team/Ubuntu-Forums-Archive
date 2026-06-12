---
title: "Synaptic error"
date: 2008-03-15
forum: General Help
---

### Post by idiocyX on 2008-03-15
hey everyone! hope someone can help me with this!
every time i open synaptic i get this error: 
[B]E: Unable to parse package file /var/lib/apt/extended_states (1)
E: _cache->open() failed, please report.
[/B]
after closing the error message, synaptic just closes itself.
when i try apt-get upgrade i get a similiar error, just in terminal output.
[B]Reading package lists... Done
Building dependency tree       
Reading state information... Error!
E: Unable to parse package file /var/lib/apt/extended_states (1)
[/B]

does anyone know what might be wrong?

---

### Post by danwood76 on 2008-03-15
a quick search reveals this thread:
[http://ubuntuforums.org/showthread.php?t=520568](http://ubuntuforums.org/showthread.php?t=520568)

so do:
```

sudo mv /var/lib/apt/extended_states /var/lib/apt/extended_states_tmp

```

---

