---
title: "Duration column in nautilus (or any other file manager)"
date: 2019-12-07
forum: General Help
---

### Post by nicklikesfire on 2019-12-07
Hello all!

I can't seem to get a duration column to display for nautilus. I've tried the instructions found here:
[https://superuser.com/questions/755690/display-audio-video-stream-title-and-duration-of-file-in-nautilus-folder](https://superuser.com/questions/755690/display-audio-video-stream-title-and-duration-of-file-in-nautilus-folder)
and in other similar help requests, but no luck.

[INDENT]~$ sudo apt-get install nautilus-columns
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
 nautilus-columns : Depends: python-kaa-metadata but it is not installable
                    Depends: python-pypdf but it is not installable
                    Depends: python-imaging but it is not installable
E: Unable to correct problems, you have held broken packages.[/INDENT]

No idea how to fix that.

I've also tried using dolphin, which has the column by default, but no lengths end up displayed.

Any ideas?

I'm using:
Ubuntu 19.04
Gnome 3.32.1

Thanks,

-Nick

---

### Post by Impavidus on 2019-12-08
The good news is, the PPA you use is still available and somewhat maintained. The bad news is, the package has 3 dependencies that are neither in the PPA nor in the official repos. python-pypdf, python-imaging and python-kaa-metadata were all dropped after 16.04. So your PPA is not that well maintained. I see very few updates after 2017 and no packages for Ubuntu releases after 17.04. So disable that PPA and try to find a different solution.

---

### Post by nicklikesfire on 2019-12-08
I found this:
[https://www.linuxuprising.com/2019/02/nautilus-exif-pdf-and-audio-metadata.html](https://www.linuxuprising.com/2019/02/nautilus-exif-pdf-and-audio-metadata.html)

But I end up with a problem where it stalls out here:

[INDENT]nick@light-up-milkcrate:/tmp/python-kaa$ sudo apt install ./*.deb
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Note, selecting 'python-kaa-base' instead of './python-kaa-base_0.6.0+svn4596-1_amd64.deb'
Note, selecting 'python-kaa-metadata' instead of './python-kaa-metadata_0.7.7+svn4596-4_amd64.deb'
The following additional packages will be installed:
  libsqlite0 python-sqlite
Suggested packages:
  python-sqlite-dbg
The following NEW packages will be installed:
  libsqlite0 python-kaa-base python-kaa-metadata python-sqlite
0 upgraded, 4 newly installed, 0 to remove and 2 not upgraded.
Need to get 181 kB/549 kB of archives.
After this operation, 2,142 kB of additional disk space will be used.
Do you want to continue? [Y/n] y
Get:1 /tmp/python-kaa/python-kaa-base_0.6.0+svn4596-1_amd64.deb python-kaa-base amd64 0.6.0+svn4596-1 [209 kB]
Get:2 /tmp/python-kaa/python-kaa-metadata_0.7.7+svn4596-4_amd64.deb python-kaa-metadata amd64 0.7.7+svn4596-4 [159 kB]
64% [Waiting for headers][/INDENT]

And I end up with:

[INDENT]nick@light-up-milkcrate:/tmp/python-kaa$ sudo apt install ./*.deb
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Note, selecting 'python-kaa-base' instead of './python-kaa-base_0.6.0+svn4596-1_amd64.deb'
Note, selecting 'python-kaa-metadata' instead of './python-kaa-metadata_0.7.7+svn4596-4_amd64.deb'
The following additional packages will be installed:
  libsqlite0 python-sqlite
Suggested packages:
  python-sqlite-dbg
The following NEW packages will be installed:
  libsqlite0 python-kaa-base python-kaa-metadata python-sqlite
0 upgraded, 4 newly installed, 0 to remove and 2 not upgraded.
Need to get 181 kB/549 kB of archives.
After this operation, 2,142 kB of additional disk space will be used.
Do you want to continue? [Y/n] y
Get:1 /tmp/python-kaa/python-kaa-base_0.6.0+svn4596-1_amd64.deb python-kaa-base amd64 0.6.0+svn4596-1 [209 kB]
Get:2 /tmp/python-kaa/python-kaa-metadata_0.7.7+svn4596-4_amd64.deb python-kaa-metadata amd64 0.7.7+svn4596-4 [159 kB]
Err:3 [http://ro-mirrors.evowise.com/ubuntu](http://ro-mirrors.evowise.com/ubuntu) disco/universe amd64 libsqlite0 amd64 2.8.17-15fakesync1build1
  Connection failed [IP: 104.19.136.75 80]
Err:4 [http://ro-mirrors.evowise.com/ubuntu](http://ro-mirrors.evowise.com/ubuntu) disco/universe amd64 python-sqlite amd64 1.0.1-12
  Connection failed [IP: 104.19.137.75 80]
E: Failed to fetch [http://ro-mirrors.evowise.com/ubuntu/pool/universe/s/sqlite/libsqlite0_2.8.17-15fakesync1build1_amd64.deb](http://ro-mirrors.evowise.com/ubuntu/pool/universe/s/sqlite/libsqlite0_2.8.17-15fakesync1build1_amd64.deb)  Connection failed [IP: 104.19.136.75 80]
E: Failed to fetch [http://ro-mirrors.evowise.com/ubuntu/pool/universe/p/python-sqlite/python-sqlite_1.0.1-12_amd64.deb](http://ro-mirrors.evowise.com/ubuntu/pool/universe/p/python-sqlite/python-sqlite_1.0.1-12_amd64.deb)  Connection failed [IP: 104.19.137.75 80]
E: Unable to fetch some archives, maybe run apt-get update or try with --fix-missing?[/INDENT]

At which point I'm not sure what to do.

---

### Post by Impavidus on 2019-12-08
The package manager attempts to install two additional packages from the official repositories (which is correct), but fails to connect to the server. I can connect to that server now, both using name and IP number (I get a different number for that name). Maybe a temporary server glitch. Try again. If problems persist, try a different mirror.

---

### Post by nicklikesfire on 2019-12-08
amazing! Thank you so much! It works!

now... any idea how to make files sortable by length? Hah.

Thank you again!

---

