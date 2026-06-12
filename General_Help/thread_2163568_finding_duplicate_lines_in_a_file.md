---
title: "finding duplicate lines in a file"
date: 2013-07-18
forum: General Help
---

### Post by karvec on 2013-07-18
Hi, I'm trying to find duplicate lines in a file, i.e.

<id>1048</id>
....

some stuff...


<id>1048</id>

But not specifically <id>1048</id>, just any matching lines.

Any suggestions on how one would accomplish this, preferably command-line (I do not have a GUI set up on my linux box.)

I know there's many ways to find duplicate files, duplicate lines in multiple files, but what about duplicate lines in the same file, matching any pattern?

Any input would be helpful.

Thank you.

---

### Post by steeldriver on 2013-07-18
how about 

```
sort *file *| uniq -d
```

---

