---
title: "init: Unable to execute &quot;/bin/sh&quot; for rcS: Permission denied"
date: 2008-04-16
forum: General Help
---

### Post by nickajeglin on 2008-04-16
Hi, I came home from school one day to see my screen completely blank so I held down the power button. Stupid I know, and when I rebooted this came up:

init: Unable to execute "/bin/sh" for rcS: Permission denied
init: rcS Process (2303) terminated with status 255
init: Unable to execute "/bin/sh" for rc-default
init: rc-default process (2304) terminated with status 255

Anyone have any idea on this before I reinstall?
I backed up my entire root directory to another computer about 3 days ago, so it won't be a huge deal, but it would be nice to find a fix. I'm running gutsy and I can't think of having done anything to set this off, unless it could come from a problem with the hibernation thing and my laptop, as someone in my family may have shut the lid on it.

---

### Post by wdaniels on 2008-04-18
Do you see any errors related to the filesystem before that?

---

### Post by pointone on 2008-04-18
If you can boot a live CD and mount the drive, check what the permissions on /bin/sh are.

```
ls /path/to/mounted/drive/bin/sh -l
```

---

### Post by nickajeglin on 2008-04-19
for some reason I don't seem to be able to boot my live cd either. I'm burning a new one to try in case it's the cd.

---

