---
title: "Cannot configure printers. Cups disaapeared"
date: 2007-02-05
forum: General Help
---

### Post by sander marechal on 2007-02-05
Cups has disappeared from my Edgy installation. When I tried to add a printer I get "The CUPS server could not be contacted". There are quite a few threads about thsi error already and the solution is always "reinstall cupsys and cupsys-client".

Well, there is no package "cupsys" in Synaptic. It's listed, but no version is available.

Synaptic: 
> 
cupsys:

Package cupsys has no available version, but exists in the database.
This typically means that the package was mentioned in a dependency and never uploaded, has been obsoleted or is not available with the contents of sources.list



apt-get install:
```

Package cupsys is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
However the following packages replace it:
  libcupsys2-dev cupsys-common cupsys-client cupsys-bsd
E: Package cupsys has no installation candidate

```

Also, there is no symlink in /etc/init.d/cups but my /etc/cups directory does exist and contains configuration files.

Now what?!

---

### Post by bapoumba on 2007-02-05
```
aptitude show cupsys
Package: cupsys
State: installed
Automatically installed: no
Version: 1.2.4-2ubuntu3
Priority: optional
Section: net

```
Could you post your sources.list ?

---

### Post by sander marechal on 2007-02-06
Here you go:

```



deb http://nl.archive.ubuntu.com/ubuntu edgy main restricted
deb-src http://nl.archive.ubuntu.com/ubuntu edgy main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb http://nl.archive.ubuntu.com/ubuntu edgy-updates main restricted
deb-src http://nl.archive.ubuntu.com/ubuntu edgy-updates main restricted

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb http://nl.archive.ubuntu.com/ubuntu edgy universe multiverse
deb-src http://nl.archive.ubuntu.com/ubuntu edgy universe multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
deb http://nl.archive.ubuntu.com/ubuntu edgy-backports main restricted universe multiverse
deb-src http://nl.archive.ubuntu.com/ubuntu edgy-backports main restricted universe multiverse

deb http://security.ubuntu.com/ubuntu edgy-security main restricted
deb-src http://security.ubuntu.com/ubuntu edgy-security main restricted

deb http://security.ubuntu.com/ubuntu edgy-security universe multiverse
deb-src http://security.ubuntu.com/ubuntu edgy-security universe multiverse

## Wine HQ
deb http://wine.budgetdedicated.com/apt edgy main

## jejik
deb http://packages.jejik.com/ubuntu dapper main

```

---

### Post by sander marechal on 2007-02-06
I used to have cupsys, but that was version 1.2.0 left over from Dapper. I removed that following the reinstall advice from the other threads. When I tried reinstalling it, it wanted to remove pretty much all desktop applications (because they all rely on >= 1.2.4). After refreshing my package lists, the 1.2.0 disappeared from my packages list.

---

### Post by sander marechal on 2007-02-06
I think my apt cache somehow got corrupted, because cypsys is listed in [http://nl.archive.ubuntu.com/ubuntu/dists/edgy/main/binary-i386/Packages.gz](http://nl.archive.ubuntu.com/ubuntu/dists/edgy/main/binary-i386/Packages.gz). How do I force APT to re-download all the full Packages.gz lists from my sources.list and generate a fresh apt-cache?

---

### Post by bapoumba on 2007-02-06
Hello, try **sudo apt-get clean**.

---

### Post by sander marechal on 2007-02-06
Nope, that didn't work :-(

---

### Post by bapoumba on 2007-02-06
That is quite strange.
Is it still installed or not ?
Just run **aptitude show cupsys** (as I did) or **apt-cache policy cupsys** if you are not used to aptitude.

---

### Post by sander marechal on 2007-02-06
Here's the output:

```

root@tweety:/etc/apt# apt-cache policy cupsys
cupsys:
  Installed: (none)
  Candidate: (none)
  Package pin: (not found)
  Version table:
     1.2.4-2ubuntu3 1001
        500 http://nl.archive.ubuntu.com edgy/main Packages

```

---

### Post by sander marechal on 2007-02-06
In the mean time I have also found a way to re-download all the package indexes from the repositories (comment out all of sources.list, update, undo commenting, update). That didn't fix it so it's not an apt-cache corruption problem.

---

