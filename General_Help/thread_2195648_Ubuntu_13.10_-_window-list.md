---
title: "Ubuntu 13.10 - window-list"
date: 2013-12-25
forum: General Help
---

### Post by linux.girl on 2013-12-25
Hi, I re-installed my computer and have to do all my little costumizations again. I used to have a window-list app on ubuntu 13.04, I would add the ppa and install, but now I am having the following error:

 sudo add-apt-repository ppa:jwigley/window-list
 window-list is an application indicator to display a list of all current open windows. Each window can be activated by selecting from from the list.
 More info: [https://launchpad.net/~jwigley/+archive/window-list](https://launchpad.net/~jwigley/+archive/window-list)
Press [ENTER] to continue or ctrl-c to cancel adding it

gpg: keyring `/tmp/tmpd2ykbb/secring.gpg' created
gpg: keyring `/tmp/tmpd2ykbb/pubring.gpg' created
gpg: requesting key 6617CF14 from hkp server keyserver.ubuntu.com
gpg: /tmp/tmpd2ykbb/trustdb.gpg: trustdb created
gpg: key 6617CF14: public key "Launchpad PPA for James Wigley" imported
gpg: Total number processed: 1
gpg:               imported: 1  (RSA: 1)
OK
me@ubuntu:~$ sudo apt-get update
E: Could not get lock /var/lib/apt/lists/lock - open (11: Resource temporarily unavailable)
E: Unable to lock directory /var/lib/apt/lists/

Any ideas?

---

### Post by linux.girl on 2013-12-25
Problem solved - another app was using the resource, waited a bit, deleted lock and now it works, pls consider this thread solved, thanks.

---

