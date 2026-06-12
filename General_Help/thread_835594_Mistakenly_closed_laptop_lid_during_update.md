---
title: "Mistakenly closed laptop lid during update"
date: 2008-06-20
forum: General Help
---

### Post by MiMs on 2008-06-20
Now I have all kinds of problems-with synaptic manager,  opening archives and editing text files. Sometimes I get "Unable to copy user's Xauthorization file".

Help will be greatly appreciated

---

### Post by geirha on 2008-06-20
Does the following command give any errors?
```
sudo aptitude update
```

If an update was interrupted, then some package might not be properly installed/configured. You usually solve this by running 
```
sudo dpkg --configure -a
```

---

### Post by MiMs on 2008-06-20
No errors at all...

---

### Post by geirha on 2008-06-20
Did the "sudo dpkg --configure -a"-command do anything?

Also, check that you're not out of space. ```
df -h
```

---

### Post by MiMs on 2008-06-20
It didn't do anything, but I managed to solve the problem. I did a complete shutdown and restarted in recovery mode, and fixed xorg. Problem seems to be solved, I'll try to boot normally and see what's happening.

---

