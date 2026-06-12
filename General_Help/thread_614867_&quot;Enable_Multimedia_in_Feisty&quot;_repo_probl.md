---
title: "&quot;Enable Multimedia in Feisty&quot; repo problems?"
date: 2007-11-16
forum: General Help
---

### Post by crisnoh on 2007-11-16
I've been working on the How To for this and am encountering issues when attempting to set up the medibuntu repo.  After adding medibuntu to the sources list I attempted to install the key using the following command:

>  wget -q [http://medibuntu.sos-sts.com/repo/medibuntu-key.gpg](http://medibuntu.sos-sts.com/repo/medibuntu-key.gpg) -O- | sudo apt-key add -

Which results in this error:

> gpg: no valid OpenPGP data found.

After this failed attempt I gave this command a try:

> sudo wget [http://www.medibuntu.org/sources.list.d/feisty.list](http://www.medibuntu.org/sources.list.d/feisty.list) -O /etc/apt/sources.list.d/medibuntu.list


Then opened up Add/Remove Programs.  After reloading the list of applications I received these errors:

Could not download all repository indexes

> The repository might be no longer available or could not be contacted because of network problems. If available an older version of the failed index will be used. Otherwise the repository will be ignored. Check your network connection and the correct writing of the repository address in the preferences.
[http://medibuntu.sos-sts.com/repo/dists/feisty/free/binary-i386/Packages.gz:](http://medibuntu.sos-sts.com/repo/dists/feisty/free/binary-i386/Packages.gz:) 404 Not Found
[http://medibuntu.sos-sts.com/repo/dists/feisty/non-free/binary-i386/Packages.gz:](http://medibuntu.sos-sts.com/repo/dists/feisty/non-free/binary-i386/Packages.gz:) 404 Not Found
[http://medibuntu.sos-sts.com/repo/dists/feisty/free/source/Sources.gz:](http://medibuntu.sos-sts.com/repo/dists/feisty/free/source/Sources.gz:) 404 Not Found
[http://medibuntu.sos-sts.com/repo/dists/feisty/non-free/source/Sources.gz:](http://medibuntu.sos-sts.com/repo/dists/feisty/non-free/source/Sources.gz:) 404 Not Found

and after closing that one:

> W: GPG error: [http://packages.medibuntu.org](http://packages.medibuntu.org) feisty Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 2EBC26B60C5A2783

All this leads me to believe that there is either a problem with the repo, or that I am somehow too stupid to follow a list of step by step instructions.

Using Feisty.

---

### Post by por100pre1 on 2007-11-16
That's the old medibuntu page, it no longer works. Add Medibuntu [this]("https://help.ubuntu.com/community/Medibuntu") way.

---

