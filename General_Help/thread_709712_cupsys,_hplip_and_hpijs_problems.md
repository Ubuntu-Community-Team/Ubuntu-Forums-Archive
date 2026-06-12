---
title: "cupsys, hplip and hpijs problems"
date: 2008-02-27
forum: General Help
---

### Post by jedson3 on 2008-02-27
I keep getting errors suggesting that these programs are not configured properly in my system: cupsys, hplip and hpijs. Tried synaptic and apt-get. Also downloaded a debian package and tried it. I am prevented by this from installing some other programs I want. How can one get around this?

jedson

---

### Post by ajgreeny on 2008-02-27
Let's see the errors you get, please.  It may then be possible to help.  To simply say you "keep getting errors" is not really very helpful if we are going to try to help you sort out the problem.

---

### Post by jedson3 on 2008-02-27
Here are two examples.
Trying to download privoxy using synaptic.

E: cupsys: subprocess post-installation script returned error exit status 1

E: hplip: dependency problems - leaving unconfigured

E: hpijs: dependency problems - leaving unconfigured


Trying to get a working copy of cupsys using sudo apt-get install cupsys

dpkg: error processing cupsys (--configure):

 subprocess post-installation script returned error exit status 1

dpkg: dependency problems prevent configuration of hplip:

 hplip depends on cupsys (>= 1.1.20); however:

  Package cupsys is not configured yet.

dpkg: error processing hplip (--configure):

 dependency problems - leaving unconfigured

dpkg: dependency problems prevent configuration of hpijs:

 hpijs depends on hplip (>= 2.7); however:

  Package hplip is not configured yet.

 hpijs depends on hplip (>= 2.7.12-0ubuntu2~gutsy1); however:

  Package hplip is not configured yet.

dpkg: error processing hpijs (--configure):

 dependency problems - leaving unconfigured

Errors were encountered while processing:

 cupsys

 hplip

 hpijs

Also I tried re-installing all those programs using synaptic and got similar results. 

Jedson

---

