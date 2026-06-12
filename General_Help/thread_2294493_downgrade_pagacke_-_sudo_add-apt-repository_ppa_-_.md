---
title: "downgrade pagacke - sudo add-apt-repository ppa: - npm"
date: 2015-09-11
forum: General Help
---

### Post by Sky_Dog on 2015-09-11
Hi all,

I have a couple of questions:

Question 1: is there a way to downgrade a package, which has been installed with "sudo add-apt-repository ppa:"? 
I installed "sudo add-apt-repository ppa:ethereum/ethereum-dev" and I would like to deinstall it.
Question 2: Is it possible to downgrade a package installed with "npm"?

I have installed several packages in Ubuntu and I have problems with a couple of them, therefore the need to downgrade them to the latest stable version.

Regards
SkyDog

---

### Post by ian-weisser on 2015-09-11
1) Uninstall the newer software.

2) Install the older version of the software, using the specific version flag of your package manager application.
For example, if using apt-get, use '=pkg_version_number'. See man apt-get.

I do not recommend PPAs to new users, or to users unfamiliar with the package manager, for precisely the reasons you are encountering.
Please file bugs with the developers so they can fix those problems.

---

### Post by Sky_Dog on 2015-09-11
Thanks a lot ian-weisser!

---

