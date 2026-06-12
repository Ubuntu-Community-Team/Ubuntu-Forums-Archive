---
title: "Syntax error: Unterminated quoted string ...once again"
date: 2013-07-02
forum: General Help
---

### Post by drxspace on 2013-07-02
I'm trying to execute these...

```
RMcmd="$(which sudo) sh -c 'umount -t vboxsf vmshare'"
$($RMcmd)
```

...but I'm getting (for 2 days now)
> 
-t: 1: -t: Syntax error: Unterminated quoted string

A little help would be appreciated

Thanks!

---

### Post by aromo on 2013-07-02
on the second line, just leave it:
$RMcmd

---

### Post by drxspace on 2013-07-03
Thanks @aromo but this didn't work :icon_frown:

Have you tried it?

---

### Post by drxspace on 2013-07-03
I think I've found a "workaround" by prefixing the command [FONT=courier new]sh -c[/FONT].

So now, this should work:
```

RMcmd="$(which sudo) sh -c 'umount -t vboxsf vmshare'"
sh -c "$RMcmd"
```

Thanks :)

---

### Post by aromo on 2013-07-03
> **drxspace said:**
> Thanks @aromo but this didn't work :icon_frown:

Have you tried it?

I tried it with bash.  Glad you found your way around.

---

