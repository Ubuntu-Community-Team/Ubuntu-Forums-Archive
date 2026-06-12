---
title: "rc2.d link to script not executing at boot"
date: 2005-09-04
forum: General Help
---

### Post by professor_chaos on 2005-09-04
Ok, I am going nuts over this, as I have been trying for the last day and a half.

My script /etc/init.d/script is...

```
#!/bin/sh

test -x /path2binary/binary || exit 0

hostn=`hostname`
binary -a $hostn 
```

I have correctly set the symlink as 
```
/etc/rc2.d/S20script -> ../init.d/script
```

I can execute is fine as ```
/etc/rc2.d/S20script
```
It just doesn't start at boot. Arrgh!!!

I would be much appreciative of any help. Thank you in advance.  :)

---

### Post by professor_chaos on 2005-09-04
bump**

---

### Post by arnieboy on 2005-09-04
[QUOTE=professor_chaos]Ok, I am going nuts over this, as I have been trying for the last day and a half.

My script /etc/init.d/script is...

```
#!/bin/sh

test -x /path2binary/binary || exit 0

hostn=`hostname`
binary -a $hostn 
```

I have correctly set the symlink as 
```
/etc/rc2.d/S20script -> ../init.d/script
```

I can execute is fine as ```
/etc/rc2.d/S20script
```
It just doesn't start at boot. Arrgh!!!

I would be much appreciative of any help. Thank you in advance.  :)[/QUOTE]


do the following:```

sudo chmod 747  /etc/rc2.d/S20script  /etc/init.d/script
```
and then reboot your comp.
make sure root is the owner of the script and symlink.

---

### Post by professor_chaos on 2005-09-04
damn it. I'm so stupid. The path to this program isn't declared until /etc/bash.bashrc and I didn't specify the full path in the script.

I should know better. Always with full path (I say to myself while I bang my head against table).

Thanks arnieboy.

---

