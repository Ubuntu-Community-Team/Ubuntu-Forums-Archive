---
title: "How to install swupd command?"
date: 2022-03-18
forum: General Help
---

### Post by satimis on 2022-03-18
Hi all,

How to install swupd command?

$ sudo swupd check-update
sudo: swupd: command not found

Please advise which package provides swupd ?

Thanks

Regards

---

### Post by GhX6GZMB on 2022-03-18
This is Ubuntu, which normally uses Synaptic as installation/update tool.
The equivalent command would be:
$ sudo apt update

If you actually want to do the upgrade, use:
$ sudo apt upgrade

---

### Post by deadflowr on 2022-03-18
swupd is a Clear Linux OS utility, I'm not sure it can be built for Ubuntu.
But you can go ahead and try building it from source here: [https://github.com/clearlinux/swupd-client/]("https://github.com/clearlinux/swupd-client/")
And then watch it probably completely fail on Ubuntu.

---

### Post by satimis on 2022-03-18
> **ml9104 said:**
> This is Ubuntu, which normally uses Synaptic as installation/update tool.
The equivalent command would be:
$ sudo apt update

If you actually want to do the upgrade, use:
$ sudo apt upgrade
Noted and thanks

Regards

---

### Post by satimis on 2022-03-18
> **deadflowr said:**
> swupd is a Clear Linux OS utility, I'm not sure it can be built for Ubuntu.
But you can go ahead and try building it from source here: [https://github.com/clearlinux/swupd-client/]("https://github.com/clearlinux/swupd-client/")
And then watch it probably completely fail on Ubuntu.
Noted and thanks

Regards

---

