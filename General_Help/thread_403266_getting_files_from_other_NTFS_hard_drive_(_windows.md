---
title: "getting files from other NTFS hard drive ( windows)"
date: 2007-04-06
forum: General Help
---

### Post by rob1101 on 2007-04-06
hello all. i currently have a 250gig hdd with windows xp installed with all my music and photos, docs, ect. and i have another 80gig hdd witch is what i am running ubuntu on. what i want to know is there any way i can just make the 250 gig show up in ubuntu and an browse the files so i can transfer them to ubuntu?

any help would be great.

---

### Post by Maestro23 on 2007-04-06
NTFS-3g. Gives read/write access to an ntfs partition. It's in the repositories now.

> sudo aptitude install ntfs-3g

Website: [http://www.ntfs-3g.org/](http://www.ntfs-3g.org/)

NTFS-3g How-To: [http://ubuntuforums.org/showthread.php?t=217009](http://ubuntuforums.org/showthread.php?t=217009)

Recent success thread: [http://ubuntuforums.org/showthread.php?t=403209](http://ubuntuforums.org/showthread.php?t=403209)

Good luck.

---

### Post by rob1101 on 2007-04-07
> **Maestro23 said:**
> NTFS-3g. Gives read/write access to an ntfs partition. It's in the repositories now.



Website: [http://www.ntfs-3g.org/](http://www.ntfs-3g.org/)

NTFS-3g How-To: [http://ubuntuforums.org/showthread.php?t=217009](http://ubuntuforums.org/showthread.php?t=217009)

Recent success thread: [http://ubuntuforums.org/showthread.php?t=403209](http://ubuntuforums.org/showthread.php?t=403209)

Good luck.

im still a little lost as on what to do?

i don't know if i have dapper or edgy, or what they are for that matter?

---

### Post by rob1101 on 2007-04-07
> **rob1101 said:**
> im still a little lost as on what to do?

i don't know if i have dapper or edgy, or what they are for that matter?

ok now that i know i have edgy i still cant get it to work i keep getting these errors


```
(gedit:7105): GnomeUI-WARNING **: While connecting to session manager:
Authentication Rejected, reason : None of the authentication protocols specified are supported and host-based authentication failed.
robert@robert-desktop:~$ gksu gedit /etc/apt/sources.list deb http://flomertens.free.fr/ubuntu/ edgy main main-all

(gedit:7124): GnomeUI-WARNING **: While connecting to session manager:
Authentication Rejected, reason : None of the authentication protocols specified are supported and host-based authentication failed.
robert@robert-desktop:~$ gksu gedit /etc/apt/sources.listdeb http://ntfs-3g.sitesweetsite.info/ubuntu/ edgy main main-all

(gedit:7151): GnomeUI-WARNING **: While connecting to session manager:
Authentication Rejected, reason : None of the authentication protocols specified are supported and host-based authentication failed.

(gedit:7151): libgnomevfs-WARNING **: trying to read a non-existing handle

```

---

### Post by Maestro23 on 2007-04-07
Open a terminal, run this command, Copy/Paste output here:

> cat /etc/apt/sources.list

---

### Post by rob1101 on 2007-04-07
```
deb http://us.archive.ubuntu.com/ubuntu/ edgy main restricted multiverse
deb-src http://us.archive.ubuntu.com/ubuntu/ edgy main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb http://us.archive.ubuntu.com/ubuntu/ edgy-updates main restricted multiverse
deb-src http://us.archive.ubuntu.com/ubuntu/ edgy-updates main restricted

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
# deb http://us.archive.ubuntu.com/ubuntu/ edgy universe
# deb-src http://us.archive.ubuntu.com/ubuntu/ edgy universe

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb http://us.archive.ubuntu.com/ubuntu/ edgy-backports main restricted universe multiverse
# deb-src http://us.archive.ubuntu.com/ubuntu/ edgy-backports main restricted universe multiverse

deb http://security.ubuntu.com/ubuntu edgy-security main restricted multiverse
deb-src http://security.ubuntu.com/ubuntu edgy-security main restricted
# deb http://security.ubuntu.com/ubuntu edgy-security universe
# deb-src http://security.ubuntu.com/ubuntu edgy-security universe

```

---

### Post by rob1101 on 2007-04-08
bump

---

### Post by GuitarRocker2562 on 2007-04-08
There is a very easy way to get this working,

try

apt-get install ntfs-config

Note: you may want to search it in Synaptic Package Manager because I am not sure I put the right name.

---

