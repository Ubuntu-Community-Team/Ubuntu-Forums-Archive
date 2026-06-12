---
title: "Lilypond problems"
date: 2006-07-04
forum: General Help
---

### Post by kloshar on 2006-07-04
Lilypond can't be neither installed, neither uninstalled ...

sudo apt-get install lilypond

> Preconfiguring packages ...
Selecting previously deselected package lilypond-data.
(Reading database ... 113178 files and directories currently installed.)
Preparing to replace lilypond-data 2.6.3-9~breezy1 (using .../lilypond-data_2.6. 3-9~breezy1_all.deb) ...
Unpacking replacement lilypond-data ...
/var/lib/dpkg/info/lilypond-data.postrm: line 23: /usr/bin/kpsewhich: No such fi le or directory
dpkg: warning - old post-removal script returned error exit status 1
dpkg - trying script from the new package instead ...
/var/lib/dpkg/tmp.ci/postrm: line 23: /usr/bin/kpsewhich: No such file or direct ory
dpkg: error processing /var/cache/apt/archives/lilypond-data_2.6.3-9~breezy1_all .deb (--unpack):
 subprocess new post-removal script returned error exit status 1
/var/lib/dpkg/tmp.ci/postrm: line 23: /usr/bin/kpsewhich: No such file or direct ory
dpkg: error while cleaning up:
 subprocess post-removal script returned error exit status 1
Unpacking lilypond (from .../lilypond_2.6.3-9~breezy1_i386.deb) ...
/var/lib/dpkg/tmp.ci/preinst: line 19: /usr/bin/kpsewhich: No such file or direc tory
dpkg: error processing /var/cache/apt/archives/lilypond_2.6.3-9~breezy1_i386.deb  (--unpack):
 subprocess pre-installation script returned error exit status 1
Errors were encountered while processing:
 /var/cache/apt/archives/lilypond-data_2.6.3-9~breezy1_all.deb
 /var/cache/apt/archives/lilypond_2.6.3-9~breezy1_i386.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)


sudo apt-get remove lilypond
> Preconfiguring packages ...
(Reading database ... 113178 files and directories currently installed.)
Preparing to replace lilypond-data 2.6.3-9~breezy1 (using .../lilypond-data_2.6.3-9~breezy1_all.deb) ...
Unpacking replacement lilypond-data ...
/var/lib/dpkg/info/lilypond-data.postrm: line 23: /usr/bin/kpsewhich: No such file or directory
dpkg: warning - old post-removal script returned error exit status 1
dpkg - trying script from the new package instead ...
/var/lib/dpkg/tmp.ci/postrm: line 23: /usr/bin/kpsewhich: No such file or directory
dpkg: error processing /var/cache/apt/archives/lilypond-data_2.6.3-9~breezy1_all.deb (--unpack):
 subprocess new post-removal script returned error exit status 1
/var/lib/dpkg/tmp.ci/postrm: line 23: /usr/bin/kpsewhich: No such file or directory
dpkg: error while cleaning up:
 subprocess post-removal script returned error exit status 1
Errors were encountered while processing:
 /var/cache/apt/archives/lilypond-data_2.6.3-9~breezy1_all.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)


sudo apt-get remove lilypond-data
> dpkg: error processing lilypond-data (--remove):
 Package is in a very bad inconsistent state - you should
 reinstall it before attempting a removal.
terminate called after throwing an instance of 'std::logic_error'
  what():  basic_string::_S_construct NULL not valid
Aborted
pzorko@workgroup:~$ Errors were encountered while processing:
 lilypond-data


How could I remove that nasty thing? :confused:

---

### Post by fdimmling on 2006-07-04
I have lilypond installed on my system. No problems.

Friedrich

---

### Post by kloshar on 2006-07-05
OK, great. :D 

And how should I remove that nasty stuff?

---

### Post by Gustav on 2006-07-05
I've looked around since I remember I've seen this before. The solution was in this thread: [http://ubuntuforums.org/showthread.php?t=103013](http://ubuntuforums.org/showthread.php?t=103013)

If you don't want to read the entire thread, just do this:```
sudo touch /usr/bin/kpsewhich
sudo chmod 777 /usr/bin/kpsewhich

sudo apt-get remove lilypond-data

sudo rm /usr/bin/kpsewhich
```And see if it works

---

