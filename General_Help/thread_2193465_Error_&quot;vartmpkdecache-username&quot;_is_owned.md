---
title: "Error: &quot;/var/tmp/kdecache-username&quot; is owned by uid 1000 instead of uid 0."
date: 2013-12-13
forum: General Help
---

### Post by silvercats on 2013-12-13
I get this when I try to run kdbg. Running Ubuntu 12.04 and I am a beginner.

---

### Post by Bashing-om on 2013-12-13
silvercats; Hi !

Is that the only instance of the error ?
do terminal code:
```

ls -la /var/tmp

```
Who owns the files ?
If only the one file is relevant; Do: Terminal code:
```

sudo chown root.root /var/tmp/kdecache-<user_name>

```where <user_name> is your actual username as in here, my user name is "sysyop":
> 
sudo chown root.root /var/tmp/kdecache-sysop


Have you been running graphical applications as root without using kdesu (ie sudo kate rather then kdesu kate) - or some other such ?

To run a graphical application always use ""kdesu" !

[INDENT][INDENT]just try'n to help
[/INDENT][/INDENT]

---

