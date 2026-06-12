---
title: "Held broken packages error on fresh install of ubuntu 22.04.2 due to libc6 version"
date: 2023-08-09
forum: General Help
---

### Post by ssnover on 2023-08-09
This might go in the Installation subforum, but I have a suspicion that it could maybe be caused by allowing packages related to the hardware on the machine to be installed in the installation menu.

I have a fresh install of Ubuntu Desktop 22.04.2 on a Dell Precision 7770. After install, I have run `apt update` and `apt upgrade` and rebooted. When I attempt to install any further packages, I get an error from apt like so:

```

$ sudo apt install zlib1g-dev
Reading package lists... Done
Building dependency tree... Done
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
 libc6-dev : Depends: libc6 (= 2.35-0ubuntu3) but 2.35-0ubuntu3.1 is to be installed
E: Unable to correct problems, you have held broken packages.

```

I can work around this and proceed with the command if I first install the exact version of libc6 called out there:

```

sudo apt install libc6=2.35-0ubuntu3

```

However, this state is really surprising for a fresh install and the two packages indicated seem like they would be compatible: i.e. anything that depends on libc6 version 2.35-0ubuntu3 should be able to utilize 2.35-0ubuntu3.1 assuming sane semantic versioning is being followed here.

---

