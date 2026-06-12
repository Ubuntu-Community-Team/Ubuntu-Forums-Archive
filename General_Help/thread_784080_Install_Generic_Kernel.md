---
title: "Install Generic Kernel"
date: 2008-05-06
forum: General Help
---

### Post by wzwilliam on 2008-05-06
I'm sorry if the question sounds too stupid, but i couldn't find a "very newbie questions" category. How can i install the generic kernel on Hardy Heron? I was trying to install the RT73 chipset built-in wireless on my laptop using this guide: [http://ubuntuforums.org/showthread.php?t=400236](http://ubuntuforums.org/showthread.php?t=400236). For some reason i don't know the driver doens't work with the rt kernel. Any help is apreciated. The driver worked fine using the same tutorial in gutsy, by the way.

---

### Post by Joeb454 on 2008-05-06
The generic kernel comes by default in all Ubuntu installs :confused:

---

### Post by wzwilliam on 2008-05-06
> **Joeb454 said:**
> The generic kernel comes by default in all Ubuntu installs :confused:
I really don't know, man, when i check on grub my options are the rt kernel, rt kernel recovery and command line.

---

### Post by cdenley on 2008-05-06
To install the generic kernel
```

sudo apt-get install linux-generic

```

To check which kernel you are currently running
```

uname -r

```

---

### Post by wzwilliam on 2008-05-07
but i don't have internet acces on my laptop, will the apt-get work properly anyway?

---

