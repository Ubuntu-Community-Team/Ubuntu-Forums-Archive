---
title: "Apt upgrade vs Apt-get upgrade"
date: 2019-07-03
forum: General Help
---

### Post by cruzer001 on 2019-07-03
Yesterday I did a *apt upgrade* because I wanted to hold back a kernel upgrade.  Well it upgraded the kernel anyhow.  I have always expected *apt full-upgrade* to do this.

I repeated the procedure with *apt-get upgrade* and the kernel was held back.

Manual pages do not address this.  Is this expected behavior?

---

### Post by deadflowr on 2019-07-03
Yes.
apt upgrade installs will install new packages, but doesn't remove packages if removal of packages is required, apt full-upgrade will do that, though.
As oppose to apt-get upgrade which will never install new packages, it only upgrades packages already installed on the system.
*man apt* explains it fairly well.
> upgrade (apt-get(8))
           upgrade is used to install available upgrades of all packages
           currently installed on the system from the sources configured via
           sources.list(5). [B]New packages will be installed if required to
           satisfy dependencies, but existing packages will never be removed.[/B]
           If an upgrade for a package requires the removal of an installed
           package the upgrade for this package isn't performed.

vs man apt-get
> upgrade
           upgrade is used to install the newest versions of all packages
           currently installed on the system from the sources enumerated in
           /etc/apt/sources.list. Packages currently installed with new
           versions available are retrieved and upgraded; [B]under no
           circumstances are currently installed packages removed, or packages
           not already installed retrieved and installed. New versions of
           currently installed packages that cannot be upgraded without
           changing the install status of another package will be left at
           their current version.[/B] An update must be performed first so that
           apt-get knows that new versions of packages are available.


---

### Post by Frogs Hair on 2019-07-03
I don't if this article clarifies the difference or creates more questions.  

[https://itsfoss.com/apt-vs-apt-get-difference/](https://itsfoss.com/apt-vs-apt-get-difference/)

---

### Post by cruzer001 on 2019-07-03
> **deadflowr said:**
> Yes.
apt upgrade installs will install new packages, but doesn't remove packages if removal of packages is required, apt full-upgrade will do that, though.
As oppose to apt-get upgrade which will never install new packages, it only upgrades packages already installed on the system.
*man apt* explains it fairly well.

vs man apt-get
Thank you for explaining that. I read it differently with my already bias assumptions :)

Thanks Frog Hair, I'll give it a read.

Solved

---

