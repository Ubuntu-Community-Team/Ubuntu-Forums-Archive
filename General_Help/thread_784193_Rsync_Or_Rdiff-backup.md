---
title: "Rsync Or Rdiff-backup ???"
date: 2008-05-06
forum: General Help
---

### Post by nami on 2008-05-06
What is better and why?

---

### Post by gilgongo on 2008-06-17
Sorry for necroposting this, but for the record, some things come to mind:

As its name suggests, rdiff-backup is (probably) better if you intend to back up files from one disk or machine to another, since it allows you to create nice incremental backups (and restore these easily as well). The slight down side is that it messes with your files on the target to do this.

If you just want to maintain a mirror/snapshot of a bunch of files, then rsync as probably more straightforward.

---

### Post by colau on 2009-06-27
> **gilgongo said:**
> Sorry for necroposting this, but for the record, some things come to mind:

As its name suggests, rdiff-backup is (probably) better if you intend to back up files from one disk or machine to another, since it allows you to create nice incremental backups (and restore these easily as well). The slight down side is that it messes with your files on the target to do this.

If you just want to maintain a mirror/snapshot of a bunch of files, then rsync as probably more straightforward.
I think, rsync also have incremental backing up option.

---

### Post by mike555 on 2009-06-28
You might want to use "Back in Time"  from;  [http://backintime.le-web.org/](http://backintime.le-web.org/)    it works good for me ..............

---

