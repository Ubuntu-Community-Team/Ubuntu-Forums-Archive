---
title: "Root access only"
date: 2007-07-02
forum: General Help
---

### Post by rmonk64 on 2007-07-02
I'm using Ubuntu 7.04. At some point, I've screwed up  my user/access configurations. When I attempt to login in as "user", I'm still in root. Somehow I've given "user" superpowers and can't figure out how to get "user" back to normal. I've tried the user settings, but no luck.

---

### Post by rillip on 2007-07-03
please post the output of 

```
groups
```

Not 100% on the syntax, it might be groups (user) or something of the like, but I think just "groups" will tell you what groups the user you are running the command as is in.

---

### Post by rmonk64 on 2007-07-03
"root adm dialout fax cdrom floppy tape audio dip plugdev scanner admin fuse"

---

