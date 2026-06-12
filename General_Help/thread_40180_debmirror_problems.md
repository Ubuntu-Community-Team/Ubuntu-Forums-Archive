---
title: "debmirror problems"
date: 2005-06-08
forum: General Help
---

### Post by aquadraht on 2005-06-08
Hi,

I'm using debmirror to have own ubuntu-mirrors in my LAN. I have problems with mirroring a few universe-packages.
I tried several sources (my default is archive.ubuntu.com) and always get the same error. I receive the error for more than 2 weeks, so it couldn't be a temporary inconsistence of the mirror servers.

Is anyone of you familiar of debmirror and can give me a hint?

My mirroring-command:
```

HOST=archive.ubuntu.com
OPTS="--bwlimit=30 -a --partial --delete"
debmirror /media/ubuntu/mirror/hoary -a i386 -v -e rsync --rsync-options="$OPTS" -h $HOST \
-d hoary --nosource -s main,restricted,multiverse,universe -r :ubuntu

```


And that's the output:

```

Mirroring to /media/ubuntu/mirror/hoary from rsync://anonymous:archive.ubuntu.com/:ubuntu/
Arches: i386
Dists: hoary
Sections: main,restricted,multiverse,universe
Download at most 200 files per rsync call.
Attempting to get lock, this might take 2 minutes before it fails.
Get Release files.
remote_get rsync dists/hoary/Release
remote_get rsync dists/hoary/Release.gpg
gpg: Signature made Fri May 13 14:42:53 2005 CEST using DSA key ID 437D05B5
gpg: Good signature from "Ubuntu Archive Automatic Signing Key <ftpmaster@ubuntu.com>"
Get Packages and Sources files and other miscellany.
Parse Packages and Sources files and add to the file list everything therein.
Cleanup mirror.
Download all files that we need to get (111 MiB).
receiving file list ... done
./
pool/universe/g/gcc-3.4/

sent 2482 bytes  received 3650 bytes  2452.80 bytes/sec
total size is 2097  speedup is 0.34
pool/universe/e/evince/evince_0.1.9-0ubuntu1_i386.deb missing
pool/universe/g/gcc-3.4/g77-3.4_3.4.3-9ubuntu4_i386.deb missing
pool/universe/g/gcc-4.0/cpp-4.0_4.0-0pre6ubuntu7_i386.deb missing
pool/universe/g/gcc-4.0/g++-4.0_4.0-0pre6ubuntu7_i386.deb missing
pool/universe/g/gcc-4.0/gcc-4.0_4.0-0pre6ubuntu7_i386.deb missing
pool/universe/g/gcc-4.0/gcj-4.0_4.0-0pre6ubuntu7_i386.deb missing
pool/universe/g/gcc-4.0/gij-4.0_4.0-0pre6ubuntu7_i386.deb missing
pool/universe/g/gcc-4.0/libgcj6-awt_4.0-0pre6ubuntu7_i386.deb missing
pool/universe/g/gcc-4.0/libgcj6-common_4.0-0pre6ubuntu7_all.deb missing
pool/universe/g/gcc-4.0/libgcj6-dev_4.0-0pre6ubuntu7_i386.deb missing
pool/universe/g/gcc-4.0/libgcj6_4.0-0pre6ubuntu7_i386.deb missing
pool/universe/o/openoffice.org2-debian-files/openoffice.org2-debian-files_1.9.76-0ubuntu1_all.deb missing
pool/universe/o/openoffice.org2/openoffice.org2-calc_1.9.79.2-0ubuntu2_i386.deb missing
pool/universe/o/openoffice.org2/openoffice.org2-common_1.9.79.2-0ubuntu2_all.deb missing
pool/universe/o/openoffice.org2/openoffice.org2-core_1.9.79.2-0ubuntu2_i386.deb missing
pool/universe/o/openoffice.org2/openoffice.org2-draw_1.9.79.2-0ubuntu2_i386.deb missing
pool/universe/o/openoffice.org2/openoffice.org2-evolution_1.9.79.2-0ubuntu2_i386.deb missing
pool/universe/o/openoffice.org2/openoffice.org2-gnome_1.9.79.2-0ubuntu2_i386.deb missing
pool/universe/o/openoffice.org2/openoffice.org2-impress_1.9.79.2-0ubuntu2_i386.deb missing
pool/universe/o/openoffice.org2/openoffice.org2-kde_1.9.79.2-0ubuntu2_i386.deb missing
pool/universe/o/openoffice.org2/openoffice.org2-l10n-en-us_1.9.79.2-0ubuntu2_all.deb missing
pool/universe/o/openoffice.org2/openoffice.org2-math_1.9.79.2-0ubuntu2_i386.deb missing
pool/universe/o/openoffice.org2/openoffice.org2-writer_1.9.79.2-0ubuntu2_i386.deb missing
pool/universe/o/openoffice.org2/openoffice.org2_1.9.79.2-0ubuntu2_i386.deb missing
pool/universe/o/openoffice.org2/python-uno_1.9.79.2-0ubuntu2_i386.deb missing
pool/universe/p/poppler/libpoppler-dev_0.1.2-0ubuntu2_i386.deb missing
pool/universe/p/poppler/libpoppler0_0.1.2-0ubuntu2_i386.deb missing
Downloaded files in 14s
Failed to download files (27 errors)!

```

It sucks, cos I almost mirrored 10GB and now I miss only 27 packages!


Thanx,
a²

---

