---
title: "Update manager will not update due to &quot;untrusted packages&quot;"
date: 2014-05-18
forum: General Help
---

### Post by Arya_Akmal on 2014-05-18
I would appreciate any help with the following:

I am running Ubuntu 12.04 LTS.

When running the update manager I get the following message:

"Requires installation of untrusted packages
The action would require the installation of packages from not authenticated sources."

The offending package is listed under "other software" and is called "python-lockfile". If I uncheck the package and run update manager again, it re-checks the offending package and attempts to download and install it, with the same result.

Is there some way I can keep the update manager from trying to update that package, and simply bring other software up to date?


Thank you.

---

### Post by Frogs Hair on 2014-05-18
Post the output of the following terminal command if any errors appear .```
 sudo apt-get update 
``` if there are no errors run the next command.```
 sudo apt-get upgrade
``` Close the update manager prior to running the commands.

---

### Post by richard76 on 2014-07-23
Is it possible to solve this problem in "senior" English, I have been using UBUNTU for at least 5 yrs but have never had such a problem before. Why is an untrusted package in the updates anyway?

---

