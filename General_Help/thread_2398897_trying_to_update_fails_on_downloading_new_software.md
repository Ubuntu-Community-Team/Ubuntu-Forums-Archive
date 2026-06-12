---
title: "trying to update fails on downloading new software"
date: 2018-08-18
forum: General Help
---

### Post by foxjazz2 on 2018-08-18
when I try these instructions:
[https://www.zdnet.com/article/how-to-upgrade-to-ubuntu-linux-18-04/](https://www.zdnet.com/article/how-to-upgrade-to-ubuntu-linux-18-04/)

it fails to download with 404.
Unsure the best way to upgrade?  Can upgrade from cd?

   E:The repository 'http://us.archive.ubuntu.com/ubuntu zesty Release' does no longer have a Release file., W:Updating from such a repository can't be done securely, and is therefore disabled by default., W:See apt-secure(8) manpage for repository creation and user configuration details., E:The repository 'http://us.archive.ubuntu.com/ubuntu zesty-updates Release' does no longer have a Release file., W:Updating from such a repository can't be done securely, and is therefore disabled by default., W:See apt-secure(8) manpage for repository creation and user configuration details., E:The repository 'http://us.archive.ubuntu.com/ubuntu zesty-backports Release' does no longer have a Release file., W:Updating from such a repository can't be done securely, and is therefore disabled by default., W:See apt-secure(8) manpage for repository creation and user configuration details., E:The repository 'http://security.ubuntu.com/ubuntu zesty-security Release' does no longer have a Release file., W:Updating from such a repository can't be done securely, and is therefore disabled by default., W:See apt-secure(8) manpage for repository creation and user configuration details., E:The repository 'http://ppa.launchpad.net/thefanclub/ubuntu-after-install/ubuntu zesty Release' does not have a Release file.

---

### Post by Yellow Pasque on 2018-08-18
You appear to be running Ubuntu 17.04 ("zesty"), so you cannot upgrade directly to Ubuntu 18.04. You probably can't even upgrade along the 17.04 -> 17.10 -> 18.04 path either since 17.10 is also EOL now.
It's time for a clean install of 18.04.1

---

