---
title: "Update Manager Problem"
date: 2007-11-11
forum: General Help
---

### Post by amvdm on 2007-11-11
I was having problems with my Brother MFC-8840DN in the scan mode. I downloaded and
installed the driver for it. Next thing I know the update icon lights up telling me I need to 
upgrade the same driver. When I try to do that I get "E:The package mfc8840dlpr needs to be reinstalled, but I can't find an archive for it." Same happens when I attempt to load
the Synaptic Package Manager, when I close the error message it also closes access to the
settings manager of SPM.

---

### Post by por100pre1 on 2007-11-11
The solution is pretty bad, you need to remove the driver, like this:

```
sudo dpkg --remove --force-remove-reinstreq mfc8840dlpr
```

BTW, Welcome to the forums!

---

### Post by amvdm on 2007-11-11
I tried your suggestion a few times and got this result:

albert@albert-laptop:~$ sudo dpkg --remove --force-remove-reinstreq mfc8840dlpr
dpkg - warning, overriding problem because --force enabled:
 Package is in a very bad inconsistent state - you should
 reinstall it before attempting a removal.
(Reading database ... 126583 files and directories currently installed.)
Removing mfc8840dlpr ...
/var/lib/dpkg/info/mfc8840dlpr.postrm: 3: /etc/init.d/lpd: not found
dpkg: error processing mfc8840dlpr (--remove):
 subprocess post-removal script returned error exit status 127
Errors were encountered while processing:
 mfc8840dlpr
albert@albert-laptop:~$ 

I also tried the Update Manager again, but still get the same error message plus an additional message:
E: Internal error opening cache (1). Please report.

---

### Post by por100pre1 on 2007-11-11
The package was in a very bad shape. Please read [this]("https://answers.launchpad.net/synaptic/+question/8337").

---

### Post by amvdm on 2007-11-11
Thank you. I went into /var/lib/dpkg/status and removed all reference to mfc8840d.
Update Manager working again.

---

