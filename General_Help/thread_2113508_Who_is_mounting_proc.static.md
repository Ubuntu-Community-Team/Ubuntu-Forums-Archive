---
title: "Who is mounting /proc/.static?"
date: 2013-02-07
forum: General Help
---

### Post by ejain on 2013-02-07
Ever since upgrading an Ubuntu 10.04 machine to 12.04 a while ago, /etc/cron.daily/standard has been generating warnings about a missing Lost+Found directory in /dev/.static/dev/.

The /etc/mtab has this:

```
/dev/sda1 /dev/.static/dev ext3 ro,relatime,errors=continue,data=writeback 0 0
```

I can `umount /dev/.static/dev`, but how do I get rid of it permanently? Who is mounting it?

---

### Post by SeijiSensei on 2013-02-07
Try "sudo lsof | grep \.static"?  That will tell the process(es) using any files with ".static" in their names.

---

### Post by ejain on 2013-02-07
> **SeijiSensei said:**
> Try "sudo lsof | grep \.static"?  That will tell the process(es) using any files with ".static" in their names.

Thanks; looks like no processes are using any files with ".static". I also did a `sudo fgrep -r \.static /etc`, which gives me this:

```
/etc/rc6.d/S40umountfs:           /|/proc|/dev|/.dev|/dev/pts|/dev/shm|/dev/.static/dev|/proc/*|/sys|/sys/*|/run|/run/*|/lib/init/rw)
/etc/init.d/umountfs:             /|/proc|/dev|/.dev|/dev/pts|/dev/shm|/dev/.static/dev|/proc/*|/sys|/sys/*|/run|/run/*|/lib/init/rw)
/etc/rc0.d/S40umountfs:           /|/proc|/dev|/.dev|/dev/pts|/dev/shm|/dev/.static/dev|/proc/*|/sys|/sys/*|/run|/run/*|/lib/init/rw)
/etc/grub.d/30_os-prober:       module /hurd/${hurd_fs}.static ${hurd_fs} --readonly \\
```

Doesn't look like any of these scripts are mounting anything to /dev/.static (not /proc/.static, sorry).

Other ideas where to look?

---

