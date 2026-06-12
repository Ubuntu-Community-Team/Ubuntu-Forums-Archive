---
title: "strange window on update"
date: 2014-03-31
forum: General Help
---

### Post by Pedroski55 on 2014-03-31
I check for updates regularly. Today I got this window. I can't believe the kernel comes from an untrusted source, or is this some kind of hack attack?

---

### Post by mcduck on 2014-04-01
you get the warning if you have any untrusted package source configured, regardless of if the package you download or update actually comes from that source or not.

Easy fix, just make sure you have imported the GPG signing keys for any extra repositories you have added. They should be visible on the "Authentication"-tab of the "Softwares & Updates" settings dialog.

---

