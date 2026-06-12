---
title: "Update problems"
date: 2019-05-19
forum: General Help
---

### Post by afrancis-ozonline on 2019-05-19
Cannot update or upgrade 17.10 when I enter the following in Terminal "sudo apt-get update && apt-get upgrade" I receive a lengthy message part of which reads "The repository 'http://au.archive , ubuntu artful Release" does not have a Release file"
Updating from such a repository, can"t be done securely, and is therefore disabled by default"
Can anyone tell me how to fix this problem?

---

### Post by wildmanne39 on 2019-05-19
That is because 17.10 has reached EOL and the repositories are no longer available, your best option is to back up your important data and do a clean install of a new version of Ubuntu, I recommend 18.04 LTS it has five years of support.

---

### Post by afrancis-ozonline on 2019-05-20
Thanks for your help.

---

### Post by rsteinmetz70112 on 2019-05-21
It is theoretically possible to load the archive repositories to do a final update and then upgrade to the next release which would be 18.04, which is an LTS version.
However that is generally recommended.

---

