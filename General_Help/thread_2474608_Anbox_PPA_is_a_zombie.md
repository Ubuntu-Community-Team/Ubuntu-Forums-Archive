---
title: "Anbox PPA is a zombie"
date: 2022-05-03
forum: General Help
---

### Post by pc-cobbler on 2022-05-03
I did something stupid. I had an 18 LTS system with Anbox installed. Then I upgraded to 20 LTS, but what I should have done was uninstall Anbox and the PPA before the upgrade. I was able to uninstall Anbox, but the PPA seems to be a zombie. How do I purge the PPA?

```

sudo ppa-purge ppa:morphis/anbox-support
Updating packages lists
E: The repository 'http://ppa.launchpad.net/morphis/anbox-support/ubuntu focal Release' does not have a Release file.
Warning:  apt-get update failed for some reason

```


UPDATE: I found the Settings-> Repositories tab in Synaptic and then selected Other Software, which displayed the two Anbox PPA lines. I was able to delete them. How do I confirm that they're gone? Does "apt-cache policy" list all PPAs, even ones disabled by the upgrade process?

---

### Post by grahammechanical on 2022-05-03
Run the apt update command and see if apt looks for the PPA repository address.

By the way, if you are still interested in using Anbox it is the Ubuntu Software store for 20.04 as a snap version. Do not install Anbox-installer as it is depreciated. I have not tried to install Anbox on 22.04 but this link might show how to do it.

[https://github.com/anbox/anbox/blob/master/docs/install.md](https://github.com/anbox/anbox/blob/master/docs/install.md)

Regards

---

### Post by pc-cobbler on 2022-05-05
Thanks for that answer. That approach does not show any of the extra PPAs, so I must have gotten rid of them.

---

