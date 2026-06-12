---
title: "How to make google earth available for other users?"
date: 2007-02-28
forum: General Help
---

### Post by xtrm_redbull on 2007-02-28
Hi there, I would like to ask if there is a way to make google earth available to other users of my pc (ubuntu 6.10 edgy eft), because I add several users in users and groups, then install google earth following the direction from this thread [http://www.ubuntuforums.org/showthread.php?t=365242&page=2&highlight=google+earth+repository]("http://www.ubuntuforums.org/showthread.php?t=365242&page=2&highlight=google+earth+repository")
and it works :) my only problems is, it is not available for other users. :confused:

Thanks for your help.

---

### Post by zanglang on 2007-03-01
Instead of doing ./GoogleEarth.bin try:
```
sudo ./GoogleEarth.bin
```
that would install it in /opt/googleearth, which would make it available for everyone. ;)

---

### Post by xtrm_redbull on 2007-03-01
Thanks zanglang, I reinstalled google-earth like you said but it didn't automatically make a short cut for other user's, but I can now access the google earth folder from the /opt/google-earth like you said so i can just make a shortcut for other user's. Thanks man:)

---

### Post by Ramses de Norre on 2007-03-01
This is a pretty neat repo with packages like googleearth:
```
## Medibuntu - Ubuntu 6.10 "edgy eft"
## Please report any bug on https://launchpad.net/products/medibuntu/+bugs
deb http://medibuntu.sos-sts.com/repo/ edgy free non-free
deb-src http://medibuntu.sos-sts.com/repo/ edgy free non-free

```
Packages installed with apt(itude) from this repo are accessible by all users.

The repo contains some potential illegal packages too though (libdvdcss2, w32codecs), so use it on your own responsibility.

---

### Post by xtrm_redbull on 2007-03-02
Thanks Ramses de Norre, for the repo, I'll check it out. :)

---

