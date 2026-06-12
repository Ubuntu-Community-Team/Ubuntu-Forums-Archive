---
title: "Problem Manually Adding Repository to 10.04 LTS Lucid"
date: 2014-04-15
forum: General Help
---

### Post by chiques on 2014-04-15
I keep running into this communication problem

> 
root@garage-server:/home/chiques# sudo add-apt-repository ppa:garhuy/lucid
gpg: keyring `/tmp/tmp4Py3a8/secring.gpg' created
gpg: keyring `/tmp/tmp4Py3a8/pubring.gpg' created
gpg: requesting key A03ADE42 from hkp server keyserver.ubuntu.com
gpgkeys: HTTP fetch error 7: couldn't connect to host
gpg: no valid OpenPGP data found.
gpg: Total number processed: 0
recv failed
root@garage-server:/home/chiques


I'm trying to follow the instruction on: [https://launchpad.net/~garhuy/+archive/lucid](https://launchpad.net/~garhuy/+archive/lucid) 

The specific step which is not working is : [https://launchpad.net/+help-soyuz/ppa-sources-list.html](https://launchpad.net/+help-soyuz/ppa-sources-list.html)


Any help is appreciated.

---

### Post by grahammechanical on 2014-04-15
Ubuntu 10.04 desktop reached end of life 9 May 2013. It could be that the maintainer of the PPA is no longer maintaining it because the Ubuntu version that it was for has reached end of life. This could be why you are getting "could not connect to host" and "no valid OpenPGP data found" messages.

Regards.

---

### Post by chiques on 2014-04-16
So it would be wise to update to the latest Ubuntu Server which is still supported?



> **grahammechanical said:**
> Ubuntu 10.04 desktop reached end of life 9 May 2013. It could be that the maintainer of the PPA is no longer maintaining it because the Ubuntu version that it was for has reached end of life. This could be why you are getting "could not connect to host" and "no valid OpenPGP data found" messages.

Regards.

---

### Post by QIII on 2014-04-16
If you are running the Lucid server version, it is still supported *by Canonical.*

However, grahammechanical's comments still apply.  If a PPA is no longer maintained for a version, this sort of thing happens.  Even though the server version of Lucid is supported by Canonical, I suspect that most PPA maintainers have moved on to newer versions.

---

### Post by chiques on 2014-04-16
So can I still update using apt-get update? 

> **QIII said:**
> If you are running the Lucid server version, it is still supported *by Canonical.*

However, grahammechanical's comments still apply.  If a PPA is no longer maintained for a version, this sort of thing happens.  Even though the server version of Lucid is supported by Canonical, I suspect that most PPA maintainers have moved on to newer versions.

---

### Post by QIII on 2014-04-16
I'd disable or remove that PPA completely, but yes.

---

