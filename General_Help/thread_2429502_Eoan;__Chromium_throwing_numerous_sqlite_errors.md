---
title: "Eoan;  Chromium throwing numerous sqlite errors"
date: 2019-10-18
forum: General Help
---

### Post by rbmorse on 2019-10-18
I'm getting tons of this and similar errors, all related to Chromium, in journalctl output.  Almost as numerous as the nxdomain non-error error messages. 

```
Oct 18 17:40:34 eoan chromium_chromium.desktop[21630]: [14888:9761:1018/174034.755464:ERROR:database.cc(1598)] Cookie sqlite error 778, errno 0: disk I/O error, sql: UPDATE cookies SET last_access_utc=? WHERE name=? AND host_key=? AND path=?
```

Is there any way to mitigate these, short of dumping Chrominum?

---

### Post by Skaperen on 2019-10-18
maybe dumping the bad disk.

---

### Post by rbmorse on 2019-10-18
Disk is fine, I think, but I installed 19.10 with the default ZFS option and maybe Chromium in the snap doesn't like that.  I wonder if Chrome has the same issue?  BRB.

---

### Post by guiverc on 2019-10-19
The I/O error makes me too think bad/failing disk, however if you're convinced it's not a IO issue on your hdd/ssd, I'd suggest `ubuntu-bug chromium-browser` to submit a bug report; at least it'll provide more detail that can be examined & if it's a bug - rectified by developers.  ([https://help.ubuntu.com/community/ReportingBugs](https://help.ubuntu.com/community/ReportingBugs))

---

### Post by rbmorse on 2019-10-19
Error doesn't manifest with Chrome-stable installed from the ppa.  To the limited extent I understand ZFS tools I don't see a problem with the drive (newish Samsung 970 Pro m.2).  I'll work up the bug report.

---

