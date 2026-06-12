---
title: "tmpfs and /var/run clarification"
date: 2017-06-02
forum: General Help
---

### Post by geekjon on 2017-06-02
I'm running 16.04 LTS, and I'm wanting to put a cache directory in memory, and I need some clarification about info I've found around the internet that may be wrong or just outdated.

I know that I can edit fstab with a line like this:
```
tmpfs /var/run/cache tmpfs defaults,size=512M 0 0

```

But is that still necessary, or can I simply create a directory in /var/run without editing fstab to accomplish the same effect?
I've read that /var/run already resides in memory. Is that correct?

---

### Post by &amp;KyT$0P# on 2017-06-02
You can check this stuff for yourself.  Run these commands -
```
ls -la /var/run
df -h
```

On my system, the first shows that [FONT=Courier New]/var/run[/FONT] is a symlink to [FONT=Courier New]/run[/FONT], and the second shows that [FONT=Courier New]/run[/FONT] is a tmpfs.

---

### Post by geekjon on 2017-06-02
Thanks. That helps a lot, but brings me to another question. On two separate Ubuntu installations, the tmpfs [FONT=courier new]/run[/FONT] are different sizes. One reports as 2.0G and the other as 780M. How do I increase the size of the smaller one?

---

### Post by geekjon on 2017-06-02
I have tried editing [FONT=courier new]/etc/fstab[/FONT] to add this line:
```

[COLOR=#000000][FONT=Menlo]tmpfs /run tmpfs defaults,size=2G 0 0[/FONT][/COLOR]
```

This seems to be working, but if there is a better way to resize [FONT=courier new]/run[/FONT] , please let me know.

---

