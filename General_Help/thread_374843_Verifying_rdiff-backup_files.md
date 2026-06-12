---
title: "Verifying rdiff-backup files"
date: 2007-03-03
forum: General Help
---

### Post by ykhun on 2007-03-03
Getting a lot of warnings with rdiff-backup 1.1.5 when trying to verify that my remote backup files are OK.

The command is issued at the command prompt of the source server, backing up to the remote destination server:

```
/usr/bin/rdiff-backup --verify --remote-schema='/usr/bin/ssh -C %s /usr/bin/rdiff-backup --server' XXX@XXX.XXX.XXX.XXX::/media/backupdrive
```

I get a ton of the following msgs, but notice that in the end, a line says that all files are verified. Is there a way to avoid these warnings? I tried the '--exclude /bin" param but it has no effect.

```
Warning: Cannot find SHA1 digest for file bin/bzcat,
perhaps because these feature was added in v1.1.1
Warning: Cannot find SHA1 digest for file bin/bzdiff,
perhaps because these feature was added in v1.1.1
Warning: Cannot find SHA1 digest for file bin/bzfgrep,
perhaps because these feature was added in v1.1.1
...
perhaps because these feature was added in v1.1.1
Warning: Cannot find SHA1 digest for file usr/share/zoneinfo/right/Universal,
perhaps because these feature was added in v1.1.1
Warning: Cannot find SHA1 digest for file usr/share/zoneinfo/right/W-SU,
perhaps because these feature was added in v1.1.1
Warning: Cannot find SHA1 digest for file usr/share/zoneinfo/right/Zulu,
perhaps because these feature was added in v1.1.1
**Every file verified successfully.**
```

---

### Post by ykhun on 2007-03-03
Just did somemore tests, it happens on a USB backup drive as well.

---

### Post by ykhun on 2007-03-08
bumped.

---

