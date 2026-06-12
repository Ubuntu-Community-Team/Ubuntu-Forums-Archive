---
title: "Dapper Package Upgrade Problem"
date: 2007-02-22
forum: General Help
---

### Post by w5pny on 2007-02-22
When running the automatic package upgrade this morning, when
it got to slocal, it would hang on trying to complete slocal.

After aborting a clearly hung condition, synaptic insisted on
doing a dpkg --configure -a manaully.  Doing that goes right
to trying to complete the slocal upgrade, but it hangs too.

What to do???

---

### Post by w5pny on 2007-02-22
I meant slocate,  not slocal!

---

### Post by MathiasHBG_SWE on 2007-02-24
I have the **exact** same problem with linux-restricted-modules-2.6.17-11-generic and no one has been able to help!

Im gonna watch this thread closely!

Ive tried purging, removing, making a new /var/cache/apt catalog and then apt-get update but nothing helps!

---

