---
title: "Restore OS (ver 18.04)"
date: 2021-11-29
forum: General Help
---

### Post by peter-1984 on 2021-11-29
Hi,
What are the main files to copy, if I expect to completely restore the OS to one other previous OS backup?

---

### Post by yancek on 2021-11-29
I think you will have to be a lot more clear as to your intent as there are countless files needed to recreate an OS install.  You would obviously need the /boot directory and there are numerous configuration files in /etc but also many, many files in other locations.

---

### Post by HermanAB on 2021-11-29
Hmm, you basically need to reinstall the old version from an old install media.

---

### Post by ActionParsnip on 2021-11-29
I suggest backing up your home folder(s) and the /etc folder. If you have manually put software on your system then back that up too. It's pretty common to use /opt but you will be aware of the location (if any)

---

### Post by guiverc on 2021-11-29
You haven't mentioned if you're talking about server or desktop.
[I]
As I mainly use desktops; I primarily worry about $HOME or my user directory; and an list of installed packages.

I store my fonts, themes etc. in system directories (which will get wiped on re-install) but I have a script install them so they're not part of my backup (if they were I'd use $HOME for them, but the files would be backed up multiple times if there; thus my usage of system wide directories[/I]).

I restore my $HOME to get my files back.  Can *clean* install the system & then run my font/theme/post-install script to add the things I like, then finally run my package install script (*which I've not done in years; as it was always installing packages I no longer used but yes existed on the prior install; so tend to peruse the output & install only those I actually use with 1 or 2 commands*).

What I now do is more manual, but gives me a *cleaner* or *leaner* system, and still takes well less than 30 mins to get operating  (*time can vary on quantity of data to restore; most my files are non-local so aren't on the system anyway*).

If I've a broken system; you can re-install the OS super-fast and fix it... I do that on boxes I keep for support purposes instead of upgrading the packages; as it completes a QA-test & achieves the upgrade of packages (*as I don't use a default mp3 player; it's easy to confirm the additional packages get re-installed & my datafiles are untouched which is part of that install test!* *ps: I'm talking about current developer releases here; currently jammy & focal [ie. next 20.04.4 ISO]*)

For servers it's different, as many server apps store *conf* files in system directories which get wiped on a re-install; so extra backups are required if server, or you're using server applications.

---

### Post by peter-1984 on 2021-11-29
Many thanks to all. Is there one concrete way to easily back up whole Ubuntu OS?

---

### Post by sudodus on 2021-11-30
If you want to backup **everything**, and not only vital parts as described in the previous helpful  replies, then I would suggest that you make a [Clonezilla image](https://clonezilla.org) of the drive. It is a directory with several files, and the big files are compressed. Clonezilla is smart enough to only backup used blocks from the partitions with file systems (and skip free blocks, so it is faster than basic cloning tools like 'dd').

The following link shows more details about Clonezilla,

[Fastest way to copy HDD - I would use Clonezilla](https://askubuntu.com/questions/958242/fastest-way-to-copy-hdd/958248#958248)

---

### Post by Impavidus on 2021-11-30
/home contains your user files, so that's not part of your OS and not included in an OS backup (you want it backed up anyway). Backups of pseudo-filesystems or temporary filesystems are pointless, so you can skip /proc, /dev, /sys, /run and /tmp. /media and /mnt are used for mounting additional device, not part of your OS. You may want backups of those, but as part of your OS backup. Other than that, you have to backup everything for a full OS backup.

Note that few people create complete OS backups. Creating a backup 100 times and restoring it once takes far more time than a single fresh install. Server applications may store some data in places like /var, so if you run such an application, you have to backup such data.

---

