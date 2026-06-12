---
title: "Mysterious files /p and /pz"
date: 2013-05-08
forum: General Help
---

### Post by CaptSaltyJack on 2013-05-08
I'm running a VPS that runs Ubuntu 12.04 Server LTS. I've just noticed two files, about 512MB each, one is called p and the other pz and they're at root level in the filesystem.

Running strings on these turns up results like this:

```

etc/
0000755
0000000
0000000
00000000000
12126634451
010333
ustar
root
root
etc/rsyslog.d/
0000755
0000000
0000000
00000000000
12123432520
012245
ustar
root
root
etc/rsyslog.d/postfix.conf
0000644
0000000

```

Does anyone know what this might be? Do I need to keep them around?

---

### Post by schragge on 2013-05-08
Looks like a tarball. Try ```
tar tvf /p
```

---

### Post by CaptSaltyJack on 2013-05-08
Good call. Now removed, now that I know these aren't important system files. :) Thanks!

---

### Post by ikt on 2013-05-08
> **schragge said:**
> Looks like a tarball. Try ```
tar tvf /p
```

How did you guess it was a tarball?

---

