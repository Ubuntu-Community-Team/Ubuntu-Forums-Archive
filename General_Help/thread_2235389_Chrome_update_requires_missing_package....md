---
title: "Chrome update requires missing package..."
date: 2014-07-20
forum: General Help
---

### Post by ofnuts on 2014-07-20
I have a Chrome update failing with:

> 
 Failed to download [http://fr.archive.ubuntu.com/ubuntu/pool/main/libi/libindicator/libindicator7_12.10.1-0ubuntu1_amd64.deb](http://fr.archive.ubuntu.com/ubuntu/pool/main/libi/libindicator/libindicator7_12.10.1-0ubuntu1_amd64.deb) 404 Not Found [IP: 91.189.91.13 80] Failed to download [http://fr.archive.ubuntu.com/ubuntu/pool/main/liba/libappindicator/libappindicator1_12.10.0-0ubuntu1_amd64.deb](http://fr.archive.ubuntu.com/ubuntu/pool/main/liba/libappindicator/libappindicator1_12.10.0-0ubuntu1_amd64.deb) 404 Not Found [IP: 91.189.91.13 80] Failed to download [http://fr.archive.ubuntu.com/ubuntu/pool/main/libi/libindicator/libindicator7_12.10.1-0ubuntu1_amd64.deb](http://fr.archive.ubuntu.com/ubuntu/pool/main/libi/libindicator/libindicator7_12.10.1-0ubuntu1_amd64.deb) 404 Not Found [IP: 91.189.91.14 80] Failed to download [http://fr.archive.ubuntu.com/ubuntu/pool/main/liba/libappindicator/libappindicator1_12.10.0-0ubuntu1_amd64.deb](http://fr.archive.ubuntu.com/ubuntu/pool/main/liba/libappindicator/libappindicator1_12.10.0-0ubuntu1_amd64.deb) 404 Not Found [IP: 91.189.91.14 80] 


Is it a problem with the Chroime update or with the archive?

---

### Post by slooksterpsv on 2014-07-20
Try running sudo apt-get update and updating your archive index. If that doesn't work, remove chrome (make sure you have firefox or that installed just in case) and reinstall it. Are you doing Chromium or Google Chrome? I had an issue similar to this one and ended up doing the latter one (remove and reinstall).

---

### Post by vasa1 on 2014-07-20
> **ofnuts said:**
> ...
Is it a problem with the Chroime update or with the archive?
Sometimes, just trying later works.

---

### Post by ofnuts on 2014-07-21
> **vasa1 said:**
> Sometimes, just trying later works.
This batch of updates has been pestering me for the last three days, so I would expect mirrors to be up-to-date by then...

---

### Post by ofnuts on 2014-07-21
> **slooksterpsv said:**
> Try running sudo apt-get update and updating your archive index. If that doesn't work, remove chrome (make sure you have firefox or that installed just in case) and reinstall it. Are you doing Chromium or Google Chrome? I had an issue similar to this one and ended up doing the latter one (remove and reinstall).

Does refresh things, but also produces many error messages like:
> 
W: Failed to fetch [http://fr.archive.ubuntu.com/ubuntu/dists/quantal/restricted/binary-amd64/Packages](http://fr.archive.ubuntu.com/ubuntu/dists/quantal/restricted/binary-amd64/Packages)  404  Not Found [IP: 91.189.91.14 80]


Looks like the French mirror is missing things?

---

### Post by deadflowr on 2014-07-21
Isn't quantal EOL?
Then the mirrors/repos are gone.

---

### Post by ofnuts on 2014-07-21
Good remark :) Is it only the mirrors or even the master repos?

---

### Post by slooksterpsv on 2014-07-22
You may find other mirrors that keep them alive, but, and I could be wrong on this, I believe they're removed after EOL or disabled.

---

### Post by deadflowr on 2014-07-22
> **slooksterpsv said:**
> You may find other mirrors that keep them alive, but, and I could be wrong on this, I believe they're removed after EOL or disabled.

Don't know about being kept alive, but the repos are generally moved to old-release repos.
But there they are, as is, from the moment the version when out of support.
So it's more of a graveyard then anything else. Not really alive in any regard. Frozen, forever more like it.

---

### Post by ofnuts on 2014-07-22
Where would I find these old-release repos? (upgrade is scheduled, I just need to find the time for this).

---

### Post by grumblebum2 on 2014-07-22
[http://askubuntu.com/questions/91815/how-to-install-software-or-upgrade-from-old-unsupported-release](http://askubuntu.com/questions/91815/how-to-install-software-or-upgrade-from-old-unsupported-release)

---

### Post by bapoumba on 2014-07-22
[http://old-releases.ubuntu.com/](http://old-releases.ubuntu.com/)

Would highly recommend you get around that delayed upgrade :)

---

### Post by ofnuts on 2014-07-22
OK, thanks all..

I intend to upgrade... but I'm aiming at 14.04, and since that's my work machine 1) I need to make sure that some stuff works really well on 14.04, and 2) I cannot be in a state where my system is unusable so it's going to be an install on a new hard disk (and some disk-swapping);

---

