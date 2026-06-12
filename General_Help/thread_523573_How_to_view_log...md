---
title: "How to view log.."
date: 2007-08-12
forum: General Help
---

### Post by iAndrew on 2007-08-12
Okay, so I booted my computer into Ubuntu, everything happens. Then on occasion it checks the mount after 21 boots or something.

I saw a [failed] instead of the usual [ok]. I want to see what failed, is there a way I can view the check mount log?

---

### Post by TheExplorer on 2007-08-12
As far as I'm concerned all logs are stored in /var/log. Dunno exactly where is the mount log but try looking into /var/log/fsck. If I find smth relevant I'll let u know.

---

### Post by TheExplorer on 2007-08-12
Btw, Ubuntu checks the integrity of the file system on a regular basis, I believe every 30th bootup. This is normal and nothing to worry about since It automatically fixes the errors.

---

### Post by TheExplorer on 2007-08-12
You may also look into var/log/dmesg for the bootup logs.

---

### Post by iAndrew on 2007-08-12
It says 21 boots.

---

