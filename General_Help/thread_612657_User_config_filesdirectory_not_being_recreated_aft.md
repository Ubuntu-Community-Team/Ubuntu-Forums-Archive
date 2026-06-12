---
title: "User config files/directory not being recreated after program reinstallation in Gutsy"
date: 2007-11-14
forum: General Help
---

### Post by Yfrwlf on 2007-11-14
Wanted a fresh set of DLLs in Wine's system32 folder, so I deleted it and did a reinstall, but it didn't come back.  So, I deleted the entire .wine folder, hoping it would come back even after a complete purge and then reinstall, but it hasn't.  Anyone know what's not letting it come back?  I even tried a```
dpkg -r --force-remove-reinstreq wine
```  I'm afraid I don't understand enough about apt-get to know why it's not refreshing all of the files.

Thanks in advance.

---

