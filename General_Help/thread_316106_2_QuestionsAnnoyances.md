---
title: "2 Questions/Annoyances"
date: 2006-12-10
forum: General Help
---

### Post by Zaggy on 2006-12-10
1: Can I mount images -easily- , without a crappy ISO only script, or a kernel module (cdemu) ?
Right now I use a vmware machine +  winxp + daemontools + share to access images.
Yes It tried Kiso, the images came out corrupt.
Oh and it costed me diskspace badly.

2: How can I stop Synaptic from hanging so very long at 'Updating Package Information' ?
Can I somehow lower the timeout value per repository?

I -do- like Ubuntu, but these annoyances make me pissed :<
I run Dapper btw.

---

### Post by Zaggy on 2006-12-10
/bump

---

### Post by chalex on 2006-12-10
> **Zaggy said:**
> 1: Can I mount images -easily- , without a crappy ISO only script, or a kernel module (cdemu) ?
Right now I use a vmware machine +  winxp + daemontools + share to access images.
Yes It tried Kiso, the images came out corrupt.
Oh and it costed me diskspace badly.

You can use the loopback device to mount ISOs.
1) Choose the mount point (e.g. `sudo mkdir /mount/iso1`)
2) Mount the iso: `sudo mount -t iso9660 -o loop filename.iso /mount/iso1`
Now you have the files under /mount/iso1
> 
2: How can I stop Synaptic from hanging so very long at 'Updating Package Information' ?
Can I somehow lower the timeout value per repository?

Does this mean you have some repositories listed in /etc/apt/sources.list that aren't working?  Try `sudo apt-get update` at the command line (while Synaptic isn't open) to see what takes so long.

---

### Post by aysiu on 2006-12-10
Don't just *try* ```
sudo apt-get update
``` Post back the output here. It sounds as if you're having networking issues.

---

### Post by ss0007 on 2006-12-10
Hi,
I have also observed some delay when updating packaging
info in Dapper. But, it's really fast in Edgy. Try it out !!

---

### Post by Zaggy on 2006-12-12
Thanks for the replies, 

The iso mount thing was just what I -not- asked for, but thanks anyway.
I'll wait for something with a frontend I can apt-get install.

The requested apt-get update output:

> zaggynl@AMD3200L:~$ sudo apt-get update
Password:
Get:1 [http://nl.archive.ubuntu.com](http://nl.archive.ubuntu.com) dapper Release.gpg [189B]
Get:2 [http://nl.archive.ubuntu.com](http://nl.archive.ubuntu.com) dapper-updates Release.gpg [191B]
Ign [http://theli.free.fr](http://theli.free.fr) dapper Release.gpg
Get:3 [http://deb.opera.com](http://deb.opera.com) etch Release.gpg [189B]
Ign [http://wine.budgetdedicated.com](http://wine.budgetdedicated.com) dapper Release.gpg
Get:4 [http://kubuntu.org](http://kubuntu.org) dapper Release.gpg [189B]
Err [http://kubuntu.org](http://kubuntu.org) dapper Release.gpg
  Error reading from server - read (104 Connection reset by peer)
Ign [http://people.ubuntu.com](http://people.ubuntu.com) ./ Release.gpg
Err [http://seveas.theplayboymansion.net](http://seveas.theplayboymansion.net) dapper-seveas Release.gpg
  Got a single header line over 360 chars
Hit [http://nl.archive.ubuntu.com](http://nl.archive.ubuntu.com) dapper Release
Get:5 [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security Release.gpg [191B]
Hit [http://nl.archive.ubuntu.com](http://nl.archive.ubuntu.com) dapper-updates Release
Get:6 [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-backports Release.gpg [191B]
Hit [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security Release
Hit [http://wine.budgetdedicated.com](http://wine.budgetdedicated.com) dapper Release
Hit [http://theli.free.fr](http://theli.free.fr) dapper Release
Hit [http://deb.opera.com](http://deb.opera.com) etch Release
Err [http://deb.opera.com](http://deb.opera.com) etch Release

Get:7 [http://kubuntu.org](http://kubuntu.org) dapper Release.gpg [189B]
Err [http://kubuntu.org](http://kubuntu.org) dapper Release.gpg
  Error reading from server - read (104 Connection reset by peer)
Ign [http://espergreen.com](http://espergreen.com) dapper Release.gpg
Get:8 [http://www.beerorkid.com](http://www.beerorkid.com) dapper Release.gpg [189B]
Ign [http://deluge.mynimalistic.net](http://deluge.mynimalistic.net) dapper Release.gpg
Hit [http://people.ubuntu.com](http://people.ubuntu.com) ./ Release
Hit [http://nl.archive.ubuntu.com](http://nl.archive.ubuntu.com) dapper/main Packages
Ign [http://seveas.theplayboymansion.net](http://seveas.theplayboymansion.net) dapper-seveas Release
Hit [http://nl.archive.ubuntu.com](http://nl.archive.ubuntu.com) dapper/restricted Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/main Packages
Get:9 [http://mirror2.ubuntulinux.nl](http://mirror2.ubuntulinux.nl) dapper-seveas Release.gpg [307B]
Get:10 [http://media.blutkind.org](http://media.blutkind.org) dapper Release.gpg [189B]
Hit [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/restricted Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/main Sources
Hit [http://nl.archive.ubuntu.com](http://nl.archive.ubuntu.com) dapper/main Sources
Hit [http://nl.archive.ubuntu.com](http://nl.archive.ubuntu.com) dapper/restricted Sources
Hit [http://nl.archive.ubuntu.com](http://nl.archive.ubuntu.com) dapper/universe Packages
Hit [http://nl.archive.ubuntu.com](http://nl.archive.ubuntu.com) dapper/multiverse Packages
Hit [http://nl.archive.ubuntu.com](http://nl.archive.ubuntu.com) dapper/universe Sources
Hit [http://nl.archive.ubuntu.com](http://nl.archive.ubuntu.com) dapper/multiverse Sources
Ign [http://wine.budgetdedicated.com](http://wine.budgetdedicated.com) dapper/main Packages
Hit [http://nl.archive.ubuntu.com](http://nl.archive.ubuntu.com) dapper-updates/main Packages
Ign [http://kubuntu.org](http://kubuntu.org) dapper Release.gpg
Get:11 [http://deb.opera.com](http://deb.opera.com) etch Release [867B]
Ign [http://deb.opera.com](http://deb.opera.com) etch Release
Ign [http://theli.free.fr](http://theli.free.fr) dapper/listen Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-backports Release
Ign [http://people.ubuntu.com](http://people.ubuntu.com) ./ Packages
Ign [http://seveas.theplayboymansion.net](http://seveas.theplayboymansion.net) dapper-seveas/all Sources
Get:12 [ftp://ftp.free.fr](ftp://ftp.free.fr) dapper Release.gpg
Hit [http://nl.archive.ubuntu.com](http://nl.archive.ubuntu.com) dapper-updates/restricted Packages
Hit [http://nl.archive.ubuntu.com](http://nl.archive.ubuntu.com) dapper-updates/main Sources
Hit [http://nl.archive.ubuntu.com](http://nl.archive.ubuntu.com) dapper-updates/restricted Sources
Hit [http://nl.archive.ubuntu.com](http://nl.archive.ubuntu.com) dapper-updates/universe Packages
Hit [http://www.beerorkid.com](http://www.beerorkid.com) dapper Release
Err [http://www.beerorkid.com](http://www.beerorkid.com) dapper Release

Hit [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/restricted Sources
Hit [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/universe Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/multiverse Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/universe Sources
Hit [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/multiverse Sources
Hit [http://deluge.mynimalistic.net](http://deluge.mynimalistic.net) dapper Release
Hit [http://nl.archive.ubuntu.com](http://nl.archive.ubuntu.com) dapper-updates/multiverse Packages
Hit [http://nl.archive.ubuntu.com](http://nl.archive.ubuntu.com) dapper-updates/universe Sources
Hit [http://nl.archive.ubuntu.com](http://nl.archive.ubuntu.com) dapper-updates/multiverse Sources
Hit [http://espergreen.com](http://espergreen.com) dapper Release
Ign [http://wine.budgetdedicated.com](http://wine.budgetdedicated.com) dapper/main Sources
Hit [http://mirror2.ubuntulinux.nl](http://mirror2.ubuntulinux.nl) dapper-seveas Release
Err [http://mirror2.ubuntulinux.nl](http://mirror2.ubuntulinux.nl) dapper-seveas Release

Get:13 [http://kubuntu.org](http://kubuntu.org) dapper Release.gpg [191B]
Err [http://kubuntu.org](http://kubuntu.org) dapper Release.gpg
  Error reading from server - read (104 Connection reset by peer)
Ign [http://deb.opera.com](http://deb.opera.com) etch/non-free Packages
Ign [http://theli.free.fr](http://theli.free.fr) dapper/listen Sources
Err [http://seveas.theplayboymansion.net](http://seveas.theplayboymansion.net) dapper-seveas/all Sources
  Got a single header line over 360 chars
Ign [http://people.ubuntu.com](http://people.ubuntu.com) ./ Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-backports/main Packages
Hit [http://media.blutkind.org](http://media.blutkind.org) dapper Release
Err [http://media.blutkind.org](http://media.blutkind.org) dapper Release

Ign [ftp://ftp.free.fr](ftp://ftp.free.fr) dapper Release.gpg
Ign [http://espergreen.com](http://espergreen.com) dapper/main Packages
Hit [http://wine.budgetdedicated.com](http://wine.budgetdedicated.com) dapper/main Packages
Ign [http://deluge.mynimalistic.net](http://deluge.mynimalistic.net) dapper/main Packages
Get:14 [http://kubuntu.org](http://kubuntu.org) dapper Release [3756B]
Ign [http://kubuntu.org](http://kubuntu.org) dapper Release
Hit [http://deb.opera.com](http://deb.opera.com) etch/non-free Packages
Hit [http://people.ubuntu.com](http://people.ubuntu.com) ./ Packages
Hit [http://theli.free.fr](http://theli.free.fr) dapper/listen Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-backports/main Sources
Get:15 [http://www.beerorkid.com](http://www.beerorkid.com) dapper Release [5402B]
Get:16 [ftp://ftp.free.fr](ftp://ftp.free.fr) dapper Release
Hit [http://wine.budgetdedicated.com](http://wine.budgetdedicated.com) dapper/main Sources
Get:17 [http://media.blutkind.org](http://media.blutkind.org) dapper Release [5402B]
Ign [http://www.beerorkid.com](http://www.beerorkid.com) dapper Release
Get:18 [http://kubuntu.org](http://kubuntu.org) dapper Release [3765B]
Ign [http://kubuntu.org](http://kubuntu.org) dapper Release
Hit [http://deluge.mynimalistic.net](http://deluge.mynimalistic.net) dapper/main Packages
Hit [http://people.ubuntu.com](http://people.ubuntu.com) ./ Sources
Hit [http://espergreen.com](http://espergreen.com) dapper/main Packages
Hit [http://theli.free.fr](http://theli.free.fr) dapper/listen Sources
Ign [http://media.blutkind.org](http://media.blutkind.org) dapper Release
Ign [http://kubuntu.org](http://kubuntu.org) dapper Release
Get:19 [http://mirror2.ubuntulinux.nl](http://mirror2.ubuntulinux.nl) dapper-seveas Release [34.2kB]
Ign [ftp://ftp.free.fr](ftp://ftp.free.fr) dapper Release
Ign [http://media.blutkind.org](http://media.blutkind.org) dapper/main Packages
Hit [http://kubuntu.org](http://kubuntu.org) dapper Release
Get:20 [ftp://ftp.free.fr](ftp://ftp.free.fr) dapper/free Packages
Hit [http://kubuntu.org](http://kubuntu.org) dapper/main Packages
Ign [http://media.blutkind.org](http://media.blutkind.org) dapper/aiglx Packages
Ign [http://www.beerorkid.com](http://www.beerorkid.com) dapper/main Packages
Hit [http://kubuntu.org](http://kubuntu.org) dapper/main Sources
Hit [http://media.blutkind.org](http://media.blutkind.org) dapper/main Packages
Ign [http://mirror2.ubuntulinux.nl](http://mirror2.ubuntulinux.nl) dapper-seveas Release
Hit [http://kubuntu.org](http://kubuntu.org) dapper/main Packages
Ign [ftp://ftp.free.fr](ftp://ftp.free.fr) dapper/free Packages
Hit [http://media.blutkind.org](http://media.blutkind.org) dapper/aiglx Packages
Get:21 [http://kubuntu.org](http://kubuntu.org) dapper/main Sources [1671B]
Ign [http://kubuntu.org](http://kubuntu.org) dapper/main Sources
Get:22 [ftp://ftp.free.fr](ftp://ftp.free.fr) dapper/non-free Packages
Hit [http://mirror2.ubuntulinux.nl](http://mirror2.ubuntulinux.nl) dapper-seveas/all Packages
Ign [http://kubuntu.org](http://kubuntu.org) dapper/main Packages
Ign [ftp://ftp.free.fr](ftp://ftp.free.fr) dapper/non-free Packages
Ign [http://www.beerorkid.com](http://www.beerorkid.com) dapper/aiglx Packages
Ign [http://kubuntu.org](http://kubuntu.org) dapper/main Sources
Get:23 [ftp://ftp.free.fr](ftp://ftp.free.fr) dapper/free Sources
Get:24 [http://kubuntu.org](http://kubuntu.org) dapper/main Packages [4380B]
Ign [http://kubuntu.org](http://kubuntu.org) dapper/main Packages
Ign [ftp://ftp.free.fr](ftp://ftp.free.fr) dapper/free Sources
Err [http://kubuntu.org](http://kubuntu.org) dapper/main Sources
  416 Unknown
Get:25 [ftp://ftp.free.fr](ftp://ftp.free.fr) dapper/non-free Sources
Err [http://kubuntu.org](http://kubuntu.org) dapper/main Packages
  404 Not Found
Hit [http://www.beerorkid.com](http://www.beerorkid.com) dapper/main Packages
Err [http://kubuntu.org](http://kubuntu.org) dapper/main Sources
  404 Not Found
Hit [http://www.beerorkid.com](http://www.beerorkid.com) dapper/aiglx Packages
Err [http://kubuntu.org](http://kubuntu.org) dapper/main Packages
  416 Unknown
Ign [ftp://ftp.free.fr](ftp://ftp.free.fr) dapper/non-free Sources
Get:26 [ftp://ftp.free.fr](ftp://ftp.free.fr) dapper/free Packages
Err [ftp://ftp.free.fr](ftp://ftp.free.fr) dapper/free Packages
  Unable to fetch file, server said 'Failed to open file.  '
Get:27 [ftp://ftp.free.fr](ftp://ftp.free.fr) dapper/non-free Packages
Err [ftp://ftp.free.fr](ftp://ftp.free.fr) dapper/non-free Packages
  Unable to fetch file, server said 'Failed to open file.  '
Get:28 [ftp://ftp.free.fr](ftp://ftp.free.fr) dapper/free Sources
Err [ftp://ftp.free.fr](ftp://ftp.free.fr) dapper/free Sources
  Unable to fetch file, server said 'Failed to open file.  '
Get:29 [ftp://ftp.free.fr](ftp://ftp.free.fr) dapper/non-free Sources
Err [ftp://ftp.free.fr](ftp://ftp.free.fr) dapper/non-free Sources
  Unable to fetch file, server said 'Failed to open file.  '
Err [ftp://cipherfunk.org](ftp://cipherfunk.org) dapper Release.gpg
  Could not connect to cipherfunk.org:21 (205.178.189.128), connection timed outFetched 46.8kB in 2m0s (388B/s)
Failed to fetch [http://seveas.theplayboymansion.net/seveas/dists/dapper-seveas/Release.gpg](http://seveas.theplayboymansion.net/seveas/dists/dapper-seveas/Release.gpg)  Got a single header line over 360 chars
Failed to fetch [ftp://cipherfunk.org/pub/packages/ubuntu/dists/dapper/Release.gpg](ftp://cipherfunk.org/pub/packages/ubuntu/dists/dapper/Release.gpg)  Could not connect to cipherfunk.org:21 (205.178.189.128), connection timed out
Failed to fetch [http://kubuntu.org/packages/kde-latest/dists/dapper/Release.gpg](http://kubuntu.org/packages/kde-latest/dists/dapper/Release.gpg)  Error reading from server - read (104 Connection reset by peer)
Failed to fetch [http://kubuntu.org/packages/koffice-latest/dists/dapper/Release.gpg](http://kubuntu.org/packages/koffice-latest/dists/dapper/Release.gpg)  Error reading from server - read (104 Connection reset by peer)
Failed to fetch [http://kubuntu.org/packages/amarok-14/dists/dapper/Release.gpg](http://kubuntu.org/packages/amarok-14/dists/dapper/Release.gpg) Error reading from server - read (104 Connection reset by peer)
Failed to fetch [http://seveas.theplayboymansion.net/seveas/dists/dapper-seveas/all/source/Sources.gz](http://seveas.theplayboymansion.net/seveas/dists/dapper-seveas/all/source/Sources.gz)  Got a single header line over 360 chars
Failed to fetch [ftp://ftp.free.fr/pub/Distributions_Linux/plf/ubuntu/plf/dists/dapper/free/binary-i386/Packages.gz](ftp://ftp.free.fr/pub/Distributions_Linux/plf/ubuntu/plf/dists/dapper/free/binary-i386/Packages.gz)  Unable to fetch file, server said 'Failed to open file.  '
Failed to fetch [http://kubuntu.org/packages/koffice-latest/dists/dapper/main/source/Sources.gz](http://kubuntu.org/packages/koffice-latest/dists/dapper/main/source/Sources.gz)  416 Unknown
Failed to fetch [http://kubuntu.org/packages/amarok-latest/dists/dapper/main/binary-i386/Packages.gz](http://kubuntu.org/packages/amarok-latest/dists/dapper/main/binary-i386/Packages.gz)  404 Not Found
Failed to fetch [ftp://ftp.free.fr/pub/Distributions_Linux/plf/ubuntu/plf/dists/dapper/non-free/binary-i386/Packages.gz](ftp://ftp.free.fr/pub/Distributions_Linux/plf/ubuntu/plf/dists/dapper/non-free/binary-i386/Packages.gz)  Unable to fetch file, server said 'Failed to open file.  '
Failed to fetch [http://kubuntu.org/packages/amarok-latest/dists/dapper/main/source/Sources.gz](http://kubuntu.org/packages/amarok-latest/dists/dapper/main/source/Sources.gz)  404 Not Found
Failed to fetch [http://kubuntu.org/packages/amarok-14/dists/dapper/main/binary-i386/Packages.gz](http://kubuntu.org/packages/amarok-14/dists/dapper/main/binary-i386/Packages.gz)  416 Unknown
Failed to fetch [ftp://ftp.free.fr/pub/Distributions_Linux/plf/ubuntu/plf/dists/dapper/free/source/Sources.gz](ftp://ftp.free.fr/pub/Distributions_Linux/plf/ubuntu/plf/dists/dapper/free/source/Sources.gz)  Unable to fetch file, server said 'Failed to open file.  '
Failed to fetch [ftp://ftp.free.fr/pub/Distributions_Linux/plf/ubuntu/plf/dists/dapper/non-free/source/Sources.gz](ftp://ftp.free.fr/pub/Distributions_Linux/plf/ubuntu/plf/dists/dapper/non-free/source/Sources.gz)  Unable to fetch file, server said 'Failed to open file.  '
Reading package lists... Done
W: GPG error: [http://deb.opera.com](http://deb.opera.com) etch Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 033431536A423791
W: GPG error: [http://www.beerorkid.com](http://www.beerorkid.com) dapper Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 31A5F97FED8A569E
W: GPG error: [http://media.blutkind.org](http://media.blutkind.org) dapper Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 31A5F97FED8A569E
W: GPG error: [http://mirror2.ubuntulinux.nl](http://mirror2.ubuntulinux.nl) dapper-seveas Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 49A120FD1135D466
W: You may want to run apt-get update to correct these problems
W: Some index files failed to download, they have been ignored, or old ones used instead.

---

### Post by jazzgossen on 2006-12-12
That is a *long* list of repositories! Are you sure you need all of them? You might also try to use another mirror than the nl.archive... ones. Try skipping the nl part, for example, if the Dutch mirrors are slow.

---

### Post by glotz on 2006-12-12
OMGROFL! No wonder it takes forever man! :lol:

---

### Post by Zaggy on 2006-12-12
What I see is, that it does every rep very fast, but stucks at a single rep.
I was wondering if I can somehow lower the timeout value per repository update attempt, so one repository cannot keep the rest waiting.

---

