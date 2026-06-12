---
title: "Connection times out with us.archive.ubuntu.com"
date: 2007-02-25
forum: General Help
---

### Post by noalternative on 2007-02-25
I keep getting connection timeouts with us.archive.ubuntu.com.  I have tried to change the mirror to archive.ubuntu.com, and I get the same problem.  Is there a problem with this repository?  It has been slow for several weeks, but now nothing.  Here is my sources.list

[INDENT]# Automatically generated sources.list
# [http://www.ubuntu-nl.org/source-o-matic/](http://www.ubuntu-nl.org/source-o-matic/)
#
# If you get GPG errors with this sources.list, locate the GPG key in this file
# and run these commands (where KEY is replaced with that key)
#
# gpg --keyserver hkp://subkeys.pgp.net --recv-keys KEY
# gpg --export --armor KEY | sudo apt-key add -

# Ubuntu supported packages
# GPG key: 437D05B5
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper main restricted
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper-updates main restricted
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security main restricted

deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper main restricted
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper-updates main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security main restricted

# Ubuntu community supported packages
# GPG key: 437D05B5
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper universe multiverse
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper-updates universe multiverse
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security universe multiverse

deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper universe multiverse
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper-updates universe multiverse
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security universe multiverse

# Ubuntu backports project
# GPG key: 437D05B5
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper-backports main restricted universe multiverse

deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper-backports main restricted universe multiverse

# Upstream Wine
deb [http://wine.budgetdedicated.com/apt](http://wine.budgetdedicated.com/apt) dapper main

deb-src [http://wine.budgetdedicated.com/apt](http://wine.budgetdedicated.com/apt) dapper main

# Medibuntu multimedia packages
# GPG key: 0C5A2783
deb [http://medibuntu.sos-sts.com/repo/](http://medibuntu.sos-sts.com/repo/) dapper free non-free

deb-src [http://medibuntu.sos-sts.com/repo/](http://medibuntu.sos-sts.com/repo/) dapper free non-free

# Canonical Commercial packages
# GPG key: 437D05B5
deb [http://archive.canonical.com](http://archive.canonical.com) dapper-commercial main

deb-src [http://archive.canonical.com](http://archive.canonical.com) dapper-commercial main

#ubuntu-lite Packages

deb [http://blueeyedcreature.net/ubuntu](http://blueeyedcreature.net/ubuntu) ./

#swiftfox

# deb [http://getswiftfox.com/builds/debian](http://getswiftfox.com/builds/debian) unstable non-free

deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) dapper-commercial main

deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper-security main restricted universe multiverse

deb [http://www.winischhofer.net/sis/debian/unstable](http://www.winischhofer.net/sis/debian/unstable) ./
deb-src [http://www.winischhofer.net/sis/debian/unstable](http://www.winischhofer.net/sis/debian/unstable) ./[/INDENT]

---

### Post by Strider on 2007-02-25
Take a look at the mirrors list ([https://wiki.ubuntu.com/Mirrors?action=show&redirect=Archive](https://wiki.ubuntu.com/Mirrors?action=show&redirect=Archive)) and pick another mirror.  I'm sure those other 2 mirrors are normally busy.

-Mike

---

### Post by dcstar on 2007-02-25
> **noalternative said:**
> I keep getting connection timeouts with **us.archive.ubuntu.com**.  I have tried to change the mirror to **archive.ubuntu.com**, and I get the same problem.  Is there a problem with this repository?  It has been slow for several weeks, but now nothing.  Here is my sources.list
......

Both of those resolve to the same IP address (91.189.89.8 ), so possibly there is a capacity issue at the moment (maybe Ubuntu is getting too popular?)

---

