---
title: "Getting a weird error while trying to access Synaptic"
date: 2007-02-10
forum: General Help
---

### Post by deathseeker148 on 2007-02-10
Currently running 6.06, I decided to look at Synaptic and try to find a good asm compiler, but it wouldn't access the packages. I get the following error:

```
E: The package sdl needs to be reinstalled, but I can't find an archive for it.
E: Internal error opening cache (1). Please report.
```

Not sure on what to do (haven't had time to fully learn Ubuntu due to school). I could try restoring one of my backups, but not sure if that would fix it.

---

### Post by taurus on 2007-02-10
Open a terminal, Applications -> Accessories -> Terminal, and run this command to see what happens.

```
sudo apt-get update
```

---

### Post by deathseeker148 on 2007-02-10
When I ran that, it went through all the repositories and "Hit" all of them. It doesn't look like there was any errors. Synaptic still won't let me access the repositories after I ran that.

---

