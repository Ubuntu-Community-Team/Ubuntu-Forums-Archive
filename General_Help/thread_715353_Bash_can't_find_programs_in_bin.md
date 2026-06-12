---
title: "Bash can't find programs in /bin"
date: 2008-03-04
forum: General Help
---

### Post by boxingnun on 2008-03-04
I'm having a weird problem. When I login to Bash, programs like ls, cp, and mv can't be found by the shell. I can see them when I go into /bin and I can still use them by typing /bin/ls etc. I started sh to see, and the programs aren't found there either, so I don't think it's a problem with the path in Bash. Does anyone know what could be going on?

---

### Post by lloyd_b on 2008-03-04
> **boxingnun said:**
> I'm having a weird problem. When I login to Bash, programs like ls, cp, and mv can't be found by the shell. I can see them when I go into /bin and I can still use them by typing /bin/ls etc. I started sh to see, and the programs aren't found there either, so I don't think it's a problem with the path in Bash. Does anyone know what could be going on?

It sure sounds like a PATH problem.  When running bash:
```
echo $PATH
```
and see if "/bin" is in there.

Lloyd B.

---

### Post by boxingnun on 2008-03-04
It was a path problem. I had fixed it, but I didn't realize that .bash_profile is only sourced when I log out/in...and not just when I start up a new terminal. Thanks.

---

