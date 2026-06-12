---
title: "sysinfo crash in edgy"
date: 2006-10-30
forum: General Help
---

### Post by dentaku65 on 2006-10-30
Can someones confirm that sysinfo is crashing on Edgy?
Launch it from the console I get this error:

```
*** stack smashing detected ***: sysinfo terminated
Aborted (core dumped)

```

---

### Post by dentaku65 on 2006-11-02
up!

---

### Post by Propwash on 2006-11-04
Doesn't work for me. Running Edgy Eft.

---

### Post by Freiburg05 on 2006-11-08
Same error here. Also running Edgy Eft. Any ideas?

---

### Post by AVH on 2006-11-10
Iget no response from "sysinfo' inthe GUI. If I run it from the terminal I get:
> alan@livingroom:~$ sysinfo
*** stack smashing detected ***: sysinfo terminated
Aborted (core dumped)
alan@livingroom:~$
What's up?

---

### Post by net_spec on 2006-11-11
I believe I went to the sysinfo website, grabbed the .RPM for fedora, aliened it and it works.

---

### Post by taxus on 2006-12-14
For your information, the [bug has been reported](https://launchpad.net/distros/ubuntu/+source/sysinfo/+bug/59378) on LaunchPad, and a debian package is available in the thread.

---

### Post by Tyche on 2007-03-11
> **taxus said:**
> For your information, the [bug has been reported](https://launchpad.net/distros/ubuntu/+source/sysinfo/+bug/59378) on LaunchPad, and a debian package is available in the thread.

Thank you for the link.  Of course, gdebi complained that the deb package wasn't in the normal sources and cautioned against installing it :lolflag:   But that was just a click-through, and the "experimental" package installed and worked just fine.

---

