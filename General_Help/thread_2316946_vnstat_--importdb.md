---
title: "vnstat --importdb"
date: 2016-03-12
forum: General Help
---

### Post by jim_deadlock on 2016-03-12
I've just reinstalled my system. I saved a copy of the original vnstat database using the --exportdb option, then I imported it on the new system (it's the same interface id as before):

```
sudo vnstat -i eno1 --force --importdb ./vnstat.bak
```

On running vnstat -m it all looks good at this point, all the original monthly totals are showing etc. However, when I try this again a minute later I find that the database has been overwritten with a new one and all the old data is gone. I've tried the --disable and --enable options before/after importing and I've also tried this immediately after importing:

```
sudo vnstat --force --rebuildtotal
```

Any suggestions?

---

### Post by jim_deadlock on 2016-03-14
Anyone...?

I don't want to dump all my accumulated traffic stats if I can help it.

---

### Post by Vergo on 2016-03-15
You'll need to stop the vnStat daemon (vnstatd) while importing or modifying any currently used databases and restart it once the changes are done. Otherwise, the daemon will use its cached data to overwrite any changes you've done.

---

### Post by jim_deadlock on 2016-03-15
I thought I was doing that with --disable and --enable but apparently not... shutting it down properly has done the trick, much appreciated!

---

### Post by Vergo on 2016-03-16
> **jim_deadlock said:**
> I thought I was doing that with --disable and --enable but apparently not...

Did the man page or some other source give you the impression that --disable and --enable would be needed in that scenario? Just asking so that I could try improve the documentation or behaviour of future versions if there's something that can currently be interpreted in multiple ways.

---

### Post by jim_deadlock on 2016-03-17
My thought process was to read the manpage and do --importdb and when that didn't work I had another look through the manpage and saw:
> 
--enable, --disable
              Enable or disable updates for  selected  interface.

So I tried that before importing but still no luck. Perhaps you could add a note about stopping vnstatd in the --importdb section of the manpage, that certainly would have helped me.

Thanks for asking, I didn't know you were the developer!

---

