---
title: "Medibuntu Repository Error"
date: 2013-10-12
forum: General Help
---

### Post by Otto-C on 2013-10-12
Using Ubuntu 12.04.3 fully up to date.

When using Update Manager to check for updates it ends with
Error message:  Failed to download repository information.

This showed up following this weeks  updates. (10-10-13).

Any workaround help appreciated.
tia
otto-c

---

### Post by kc1di on 2013-10-12
Hello Otto-C,

Medibuntu Repository is no longer active, See[ here.]("http://www.medibuntu.org/")

---

### Post by Otto-C on 2013-10-12
kc1di
 I understand the repository is no longer active.

My question is how to stop update manager from
trying to access the repository?

tia
otto-c

---

### Post by philinux on 2013-10-12
Open Software Sources and remove them.

---

### Post by Otto-C on 2013-10-12
philinux,

Did as you suggested and removed 2 items installed. I rebooted the
machine and went to update manager and did a check. Again got the
error message: Failed to download repository information.
Below is the details of the failure:

W:Failed to fetch [http://packages.medibuntu.org/dists/precise/Release.gpg](http://packages.medibuntu.org/dists/precise/Release.gpg)  Something wicked happened resolving 'packages.medibuntu.org:http' (-5 - No address associated with hostname)
, W:Failed to fetch [http://packages.medibuntu.org/dists/precise/free/binary-i386/Packages](http://packages.medibuntu.org/dists/precise/free/binary-i386/Packages)  Something wicked happened resolving 'packages.medibuntu.org:http' (-5 - No address associated with hostname)
, W:Failed to fetch [http://packages.medibuntu.org/dists/precise/non-free/binary-i386/Packages](http://packages.medibuntu.org/dists/precise/non-free/binary-i386/Packages)  Something wicked happened resolving 'packages.medibuntu.org:http' (-5 - No address associated with hostname)
, W:Failed to fetch [http://packages.medibuntu.org/dists/precise/free/i18n/Translation-en](http://packages.medibuntu.org/dists/precise/free/i18n/Translation-en)  Something wicked happened resolving 'packages.medibuntu.org:http' (-5 - No address associated with hostname)
, W:Failed to fetch [http://packages.medibuntu.org/dists/precise/non-free/i18n/Translation-en](http://packages.medibuntu.org/dists/precise/non-free/i18n/Translation-en)  Something wicked happened resolving 'packages.medibuntu.org:http' (-5 - No address associated with hostname)
, E:Some index files failed to download. They have been ignored, or old ones used instead.

---

### Post by germanix on 2013-10-12
Try the following in the terminal:

$ sudo rm /etc/apt/sources.list.d/medibuntu.list 
Then press <enter>

This should remove the Medibuntu ppa from software sources. You may have to restart for it to take effect.

---

### Post by Otto-C on 2013-10-12
germanix

That did the job.
Thanks

Will mark as solved.

---

