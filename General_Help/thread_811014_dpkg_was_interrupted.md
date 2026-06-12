---
title: "dpkg was interrupted"
date: 2008-05-28
forum: General Help
---

### Post by nick09 on 2008-05-28
```

E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. 
E: _cache->open() failed, please report.

```

This happened after I try installing frostwire and frostwire gave me an error about not having the 1.4.0 java and I have 1.6.0 java.

Also I get this error when I try to run frostwire:
```

Something went wrong with FrostWire.
Maybe you're using the wrong version of Java?
(FrostWire is tested against and works best with with Sun's JRE, Java 1.4+)
The version of Java in your PATH is:
java version "1.6.0"
OpenJDK Runtime Environment (build 1.6.0-b09)
OpenJDK 64-Bit Server VM (build 1.6.0-b09, mixed mode)

```

---

### Post by oilchangeguy on 2008-05-28
> **nick09 said:**
> ```

E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. 
E: _cache->open() failed, please report.

```

This happened after I try installing frostwire and frostwire gave me an error about not having the 1.4.0 java and I have 1.6.0 java.

open a terminal (command line) and type, sudo dpkg --configure -a then press enter.

---

### Post by nick09 on 2008-05-28
> **oilchangeguy said:**
> open a terminal (command line) and type, sudo dpkg --configure -a then press enter.

Thats done so now what?

EDIT: I now can add programs via the repos but I still can't run frostwire.

---

### Post by oilchangeguy on 2008-05-28
> **nick09 said:**
> Thats done so now what?

go back and complete whatever it was you were doing when you got the error message.

---

### Post by nick09 on 2008-05-28
I edited my post while you were posting.

EDIT: solved it.

For 64-bit users use:
sudo update-alternatives --config java

to switch to 32-bit java.

---

