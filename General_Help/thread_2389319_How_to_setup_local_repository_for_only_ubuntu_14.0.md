---
title: "How to setup local repository for only ubuntu 14.04 e 16.04 only"
date: 2018-04-15
forum: General Help
---

### Post by jimbox80 on 2018-04-15
We are trying to set up a a repo Sever for all the distro we have. We are forced to use a Red Hat as OS so i'm looking if there is a way to create a local repo for ubuntu but only for the distro we have,* Trusty* and* Xenial.* So using not specific command for debian based system like apt-mirror.
Just looking on the folder structure of a i understood that the binary are all under the pool folder...correct?

[HTML]
dists +
         - trusty
         - trusty-backports
               .
               .
         - xenial
               . 
               .
         - artful

indices
pool
Poject
[/HTML]
       

I'm just starting to work with repo so i was thinking to use rsync i would be forced to copy all the repositories using a lot of storage. There is a way to mirror only some specific  repos based on distro i use?

---

### Post by TheFu on 2018-04-15
I use apt-cacher-ng, but don't think that is what you've described.  Since I don't have 50 identical servers, the ability of the cache to already have packages required is limited.  I'm seeing about 60% cache hits, so 40% aren't there when needed.

---

### Post by jimbox80 on 2018-04-15
just to be sure, if i could use a ubuntu VM  to create a copy with the repo i need, just configuring apt-mirror in the correct way i could easely have the repo for just the xenial and trusty distro?

---

### Post by TheFu on 2018-04-15
I've never used apt-mirror. Sorry.

apt-cacher-ng understands different distros and keeps their packages separate. I think it only works with debian-based distros.

---

### Post by HermanAB on 2018-04-16
Here is a guide - scroll down to the Ubuntu section:
[https://www.aeronetworks.ca/2016/02/mirror-mirror-on-wall.html](https://www.aeronetworks.ca/2016/02/mirror-mirror-on-wall.html)

Basically, EVERYTHING goes into a single pool.  The packages for different releases are tracked in a index file.

---

