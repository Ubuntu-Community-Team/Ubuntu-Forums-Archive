---
title: "g-io-error-guark Ubuntu's &quot;Backup&quot; fail"
date: 2016-06-03
forum: General Help
---

### Post by Mark_in_Hollywood on 2016-06-03
Re-opened as I continue to get g-10-error-quark errors. 25 Aug 16 is about splicing.

I backup weekly to an external SATA drive. For the past several backup days, I get errors. In the past I have rebooted and resolved the immediate backup fail. But as this is now persistent, I want to know how to fix this, please.

Full message reads:

Backup Failed

Giving up after 5 attempts. Error: g-io-error-quark: Error opening file: '/media/mark/80cb5313-35a0-432b-9250-4cc62d79a3c8/duplicity-inc.20160528T201042Z.to.20160603T203335Z.vol2.difftar.gpg': Read-only file system (21)

The g-io-error-quark seems to relate to a sub-folder on my /home. That folder is "/.google". I have added the .google to the "Folders to Ignore" list. The backup  ran and completed after that. 

While this isn't "solved" as I would like to do a complete backup of /home, I'm marking it as solved for now.

---

