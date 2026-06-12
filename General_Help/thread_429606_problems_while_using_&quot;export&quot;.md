---
title: "problems while using &quot;export&quot;"
date: 2007-05-01
forum: General Help
---

### Post by jojo.jojo on 2007-05-01
Hi everybody,
I tried to use export on a terminal to assume a different kernel version, but after exporting the key i can't use the terminal anymore.
The exact command I issued is:
$ export LD_ASSUME_KERNEL=2.2.5

and then every command i use give me some errors like:

/bin/bash: error while loading shared libraries: libdl.so.2: cannot open shared object file: No such file or directory

 or

ls: error while loading shared libraries: librt.so.1: cannot open shared object file: No such file or directory

end so on..

any help?
thanx!

jojo

---

### Post by jackn on 2007-05-01
Hope this is not silly, as I know zilch about kernels.

Yet, it seems to me that a live CD boot, and restarting from the live CD, will take care of the issue, as the new boot won't have the exprted variable (not yet in config files, I assume).

Is that at all useful, or are you looking to get your exported variable to work?!...

Jackn

---

