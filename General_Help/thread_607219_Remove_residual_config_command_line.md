---
title: "Remove residual config command line"
date: 2007-11-08
forum: General Help
---

### Post by stchman on 2007-11-08
Hello all I have a package question.

If I type the following:
```
sudo apt-get remove --purge <packagename>
```

Will that remove dependencies and remove the residual config as well?

Would this be a better command:
```
sudo apt-get autoremove --purge <packagename>
```

I know that autoremove will remove dependencies in Edgy or later but does not remove the residual config.

Is there also a command that will remove all residual packages?

Thanks.

---

### Post by Maestro23 on 2007-11-08
Two good docs on Apt-get & Aptitude.

Aptitude:[https://help.ubuntu.com/community/AptitudeSurvivalGuide?highlight=%28Aptitude%29](https://help.ubuntu.com/community/AptitudeSurvivalGuide?highlight=%28Aptitude%29)

Apt-Get: [https://help.ubuntu.com/community/AptGetHowto?highlight=%28get%29%7C%28apt%29](https://help.ubuntu.com/community/AptGetHowto?highlight=%28get%29%7C%28apt%29)

---

### Post by supernovus on 2008-06-13
If you want to remove all of the residual config files without using Synaptic (say for instance on a server install) then install 'wajig' then use this script:

```

#!/bin/sh

for package in `grep -B1 config-files /var/lib/dpkg/status | grep -v -- '--' | grep -v 'Status:' | awk '{ print $2 }' `; do
    echo "Removing $package residual config files"
    wajig purge $package
done

```

YMMV

---

