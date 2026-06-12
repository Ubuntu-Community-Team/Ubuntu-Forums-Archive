---
title: "Can't install upgrades or new programmes"
date: 2007-05-06
forum: General Help
---

### Post by Andersnp on 2007-05-06
Hey all. I use ubuntu 7.04.
I've got a hugh problem. When I try to use Package manager, update manager etc. I got the following error: 
E: The package limewire-basic needs to be reinstalled, but I can't find an archive for it.
E: Internal error opening cache (1). Please report.

I've tried to use the apt-get command to reinstall the package, but it seems that it won't work either. I am thinking about to reinstall ubuntu, but im not happy about it. Is it anything I can do???

---

### Post by zvacet on 2007-05-06
```
sudo apt-get remove --purge file_name
```

 file_name = correct name of your lime wire. This command will remove limewire.

---

### Post by Andersnp on 2007-05-06
OK, i did that, but it still gives me the error-code. I think I removed limewire before I got the error messages.

---

### Post by FlashDude on 2007-07-01
I have the exact same problem,  Does anyone know how to fix this??  After I run sudo apt-get for limewire the same error message shows up in the console.

---

