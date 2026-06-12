---
title: "Unable to install package in Ubuntu 10.04 LTS due to dpkg errors"
date: 2014-02-07
forum: General Help
---

### Post by AMIT_RAJ_VARMA on 2014-02-07
Hi

We  have Ubuntu 10.04 LTS setup

"Linux ZIN52RFID-02 2.6.32-33-generic #70-Ubuntu SMP Thu Jul 7 21:13:52 UTC 2011 x86_64 GNU/Linux"

Whenever we try to install package, following error is displayed.

> Unpacking replacement gnome-applets ...
dpkg: warning: old post-removal script returned error exit status 245
dpkg - trying script from the new package instead ...
dpkg: error processing /var/cache/apt/archives/gnome-applets_2.30.0-0ubuntu2_amd64.deb (--unpack):
 subprocess new post-removal script returned error exit status 245
dpkg: error while cleaning up:
 subprocess new post-removal script returned error exit status 245
Processing triggers for man-db ...
Errors were encountered while processing:
 /var/cache/apt/archives/gnome-applets_2.30.0-0ubuntu2_amd64.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)



We tried running update still we are getting, Can you suggest some solution for the same

Regards

Amit

---

### Post by jeanjd63 on 2014-02-07
Hello
You can try this :
[B]sudo  apt-get  clean
sudo  apt-get  update
sudo  apt-get  upgrade
[/B]
You have to see [this link]("http://askubuntu.com/questions/91815/how-to-install-software-or-upgrade-from-old-unsupported-release")  for old-releases 
Bye

---

