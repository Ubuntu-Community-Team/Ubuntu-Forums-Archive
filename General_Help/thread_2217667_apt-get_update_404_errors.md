---
title: "apt-get update 404 errors?"
date: 2014-04-18
forum: General Help
---

### Post by linfan on 2014-04-18
I am trying to install the Elementary OS Desktop and have added the repo but on update I get the following error:

 Failed to fetch [http://ppa.launchpad.net/elementary-os/stable/ubuntu/dists/saucy/main/binary-amd64/Packages](http://ppa.launchpad.net/elementary-os/stable/ubuntu/dists/saucy/main/binary-amd64/Packages)  404  Not Found

---

### Post by sdowney717 on 2014-04-18
Since Trusty just released, maybe they are not ready with the packages?

What version ubuntu are you using?

---

### Post by mcduck on 2014-04-18
Based on the URL of the repository it's trying to access, I assume you are using Saucy (Ubuntu 13.10)?

The last Ubuntu version supported by that PPA is 13.04, so it doesn't have any packages for your version.

---

