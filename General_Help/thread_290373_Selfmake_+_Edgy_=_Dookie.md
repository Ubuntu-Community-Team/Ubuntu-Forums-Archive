---
title: "Selfmake + Edgy = Dookie?"
date: 2006-11-01
forum: General Help
---

### Post by hikaricore on 2006-11-01
i've had about 1/3 success rate installing applications and games from selfmake binaries since upgrading to edgy.  I'm just curious if anyone else has had troubles.  So far I can't install:

ET (Enemey Territory)
ET-F
True Combat
and a couple I can't remember

and now the one that takes the cake, the Rune Demo.

```
[hikaricore@devistate:/tmp]$ sudo /home/hikaricore/.loki/loki_update/tmp/rune-demo.run
Verifying archive integrity...tail: Warning: "+number" syntax is deprecated, please use "-n +number"
OK
Uncompressing Rune Demotail: Warning: "+number" syntax is deprecated, please use "-n +number"
.............................................................................................................................................................................
loki_patch: dynamic-link.h:57: elf_get_dynamic_info: Assertion `! "bad dynamic tag"' failed.
Aborted (core dumped)
The program returned an error code (1)
```

Everything else I've just found another way to install, either from compressed archives, old installations or source.  The only problem is, as far as I can find it's not availible from any other medium.  I originally tried to install it from the Loki Demo Updater, which died a horrible death.  Then I tracked down where it downloaded the binary installer to and still no dice (as seen above).  Anyway just looking for some suggestions or to atleast know it's not just me.  :)

--Aaron

---

### Post by hikaricore on 2006-11-02
ok then.. guess it is just me :P

---

### Post by n0kS on 2008-03-22
Same problem with Gutsy trying with Heavy Gears 2 ......
```
root@n0ks-desktop:/home/n0ks/Desktop# ./hg2-demo.run 
Verifying archive integrity...tail: Warning: "+number" syntax is deprecated, please use "-n +number"
OK
Uncompressing Heavy Gear II Demotail: Warning: "+number" syntax is deprecated, please use "-n +number"
..................................................................................................................................
loki_patch: dynamic-link.h:57: elf_get_dynamic_info: Assertion `! "bad dynamic tag"' failed.
Aborted (core dumped)
The program returned an error code (1)
```

From your post has passed a lot of time, expecting someone have solution for this....

---

