---
title: "dpkg error message!"
date: 2007-03-27
forum: General Help
---

### Post by Marszster on 2007-03-27
Hello there, I am a less-than-a-week-old user of Ubuntu, and so far I haven't had any noticeable problems. However, it seems that at certain times when I access terminal and tell it to update something for me, I get an error message that says:

> E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem.

This also occurred when I tried to synchronize my clock with the time server, after it asked me to first install NAT support. Can anyone offer me some advice? Pretty much anything at this point would be appreciated.

---

### Post by simonn on 2007-03-27
Yerp, the following should solve the problem :):

```

$ sudo dpkg --configure -a

```

---

### Post by Marszster on 2007-03-29
> **simonn said:**
> Yerp, the following should solve the problem :):

```

$ sudo dpkg --configure -a

```

Tried that, and after entering my password it said I needed an action option, followed by a list of dpkg help topics (none of which answered my question.)

::EDIT::

I actually put a space between -- and configure, which is why it didn't read it. when I typed it in properly, this message came up:

> dpkg: failed to open package info file `/var/lib/dpkg/status' for reading: No such file or directory

---

