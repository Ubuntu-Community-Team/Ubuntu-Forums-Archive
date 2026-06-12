---
title: "How can remove these warnings??"
date: 2012-11-22
forum: General Help
---

### Post by Mohan1289 on 2012-11-22
```
W: GPG error: http://www.duinsoft.nl debs Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY E18CE6625CB26B26
W: Failed to fetch cdrom://Ubuntu 12.04.1 LTS _Precise Pangolin_ - Release i386 (20120817.3)/dists/precise/main/binary-i386/Packages  Please use apt-cdrom to make this CD-ROM recognized by APT. apt-get update cannot be used to add new CD-ROMs

W: Failed to fetch cdrom://Ubuntu 12.04.1 LTS _Precise Pangolin_ - Release i386 (20120817.3)/dists/precise/restricted/binary-i386/Packages  Please use apt-cdrom to make this CD-ROM recognized by APT. apt-get update cannot be used to add new CD-ROMs

W: Failed to fetch http://extras.ubuntu.com/ubuntu/dists/precise/main/binary-i386/Packages  403  Forbidden: category denied

E: Some index files failed to download. They have been ignored, or old ones used instead.
```

---

### Post by Lars Noodén on 2012-11-22
You have to find the repository's key and add it to your keychain.  The instructions will be something like this:
[http://www.duinsoft.nl/packages.php](http://www.duinsoft.nl/packages.php)

---

### Post by Mohan1289 on 2012-11-22
> **Lars Noodén said:**
> You have to find the repository's key and add it to your keychain.  The instructions will be something like this:
[http://www.duinsoft.nl/packages.php](http://www.duinsoft.nl/packages.php)

Can't we do this via Terminal??

---

### Post by Vaphell on 2012-11-22
from the linked page
```
sudo apt-key adv --keyserver keys.gnupg.net --recv-keys 5CB26B26
```

you apparently have ubuntu cd in your software sources. Disable it.

---

### Post by Mohan1289 on 2012-11-22
> **Vaphell said:**
> from the linked page
```
sudo apt-key adv --keyserver keys.gnupg.net --recv-keys 5CB26B26
```

you apparently have ubuntu cd in your software sources. Disable it.

how can i disable it?? i mean i donno what to delete so i just kept those like that here is my sources file..

```

deb cdrom:[Ubuntu 12.04.1 LTS _Precise Pangolin_ - Release i386 (20120817.3)]/ precise main restricted

# See http://help.ubuntu.com/community/UpgradeNotes for how to upgrade to
# newer versions of the distribution.
deb http://archive.ubuntu.com/ubuntu precise main restricted
deb-src http://archive.ubuntu.com/ubuntu precise main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb http://archive.ubuntu.com/ubuntu precise-updates main restricted
deb-src http://archive.ubuntu.com/ubuntu precise-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
deb http://archive.ubuntu.com/ubuntu precise universe
deb-src http://archive.ubuntu.com/ubuntu precise universe
deb http://archive.ubuntu.com/ubuntu precise-updates universe
deb-src http://archive.ubuntu.com/ubuntu precise-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb http://archive.ubuntu.com/ubuntu precise multiverse
deb-src http://archive.ubuntu.com/ubuntu precise multiverse
deb http://archive.ubuntu.com/ubuntu precise-updates multiverse
deb-src http://archive.ubuntu.com/ubuntu precise-updates multiverse

## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
deb http://archive.ubuntu.com/ubuntu precise-backports main restricted universe multiverse
deb-src http://archive.ubuntu.com/ubuntu precise-backports main restricted universe multiverse

deb http://archive.ubuntu.com/ubuntu precise-security main restricted
deb-src http://archive.ubuntu.com/ubuntu precise-security main restricted
deb http://archive.ubuntu.com/ubuntu precise-security universe
deb-src http://archive.ubuntu.com/ubuntu precise-security universe
deb http://archive.ubuntu.com/ubuntu precise-security multiverse
deb-src http://archive.ubuntu.com/ubuntu precise-security multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository.
## This software is not part of Ubuntu, but is offered by Canonical and the
## respective vendors as a service to Ubuntu users.
deb http://archive.canonical.com/ubuntu precise partner
# deb-src http://archive.canonical.com/ubuntu precise partner

## Uncomment the following two lines to add software from Ubuntu's
## 'extras' repository.
## This software is not part of Ubuntu, but is offered by third-party
## developers who want to ship their latest software.
deb http://extras.ubuntu.com/ubuntu precise main
# deb-src http://extras.ubuntu.com/ubuntu precise main


```

---

### Post by Lars Noodén on 2012-11-22
Comment out the line that starts with "deb cdrom"

---

### Post by Bashing-om on 2012-11-22
To follow directive irt CD source list->
12.04 version : launcher->top toolbar menu ->edit ->select Software Sources ->
pop-up application: window: "installable from CD_ROM/DVD" uncheck the box.

Continue with other advise. Read the link provided.
[INDENT]reading is good <== BDQ
[/INDENT]

---

### Post by Mohan1289 on 2012-11-22
> **Lars Noodén said:**
> Comment out the line that starts with "deb cdrom"

i did that and ran apt-get update
but still there are several warning and the key isn't downloading
it is showing errors.

when i ran sudo apt-get update
```


W: GPG error: http://www.duinsoft.nl debs Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY E18CE6625CB26B26
W: Failed to fetch http://extras.ubuntu.com/ubuntu/dists/precise/main/binary-i386/Packages  403  Forbidden: category denied

E: Some index files failed to download. They have been ignored, or old ones used instead.
```

and what are the errors in the update that i want to know.. how can know that and how can i rectify them?

and when i ran the command 

```

/etc/apt/sources.list.d$ sudo apt-key adv --keyserver keys.gnupg.net --recv-keys 5CB26B26

```

the output is

```
krishna@ubuntu:/etc/apt/sources.list.d$ sudo apt-key adv --keyserver keys.gnupg.net --recv-keys 5CB26B26
Executing: gpg --ignore-time-conflict --no-options --no-default-keyring --secret-keyring /tmp/tmp.9PLGy55Alk --trustdb-name /etc/apt/trustdb.gpg --keyring /etc/apt/trusted.gpg --primary-keyring /etc/apt/trusted.gpg --keyserver keys.gnupg.net --recv-keys 5CB26B26
gpg: requesting key 5CB26B26 from hkp server keys.gnupg.net
gpg: keyserver timed out
gpg: keyserver receive failed: keyserver error
```

---

