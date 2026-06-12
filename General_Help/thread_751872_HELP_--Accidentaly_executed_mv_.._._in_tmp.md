---
title: "HELP --Accidentaly executed mv ../* . in /tmp"
date: 2008-04-11
forum: General Help
---

### Post by rakeshou on 2008-04-11
Please help me, Its urgent.

I was in /tmp directory

and I accidentally executed as root

```
mv ../* .
```

in /tmp directory when it was supposed to be executed in some other directory.

Now none of my commands are working. 

I tried setting up the path as:
```

export PATH=$PATH:/tmp/bin:/tmp/sbin:/tmp/usr/sbin:/tmp/usr/bin
```

but doesnt find mv, ls commands

I also tried to execute

```
/tmp/bin/mv /tmp/bin /tmp
```

but didnt work either.

Please Help me. I am not rebooting the system, as I know it will not boot... :(

HEEEEEELLLLLLLLLPPPPPPPPPPP

---

### Post by rakeshou on 2008-04-11
I have rebooted the system, now what?
how can I restore my directories and boot again normally.

Please HELP

---

### Post by sdennie on 2008-04-11
It's possible that none of your commands will run even if they are in your path because it can't find the proper shared libraries.  It may be easier to boot into a live CD to fix your system (like the installer CD).  You can just boot up, mount the root partition and move stuff back to the root directory of that partition.

---

