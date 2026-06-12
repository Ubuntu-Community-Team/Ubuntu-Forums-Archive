---
title: "Tar.gz installation problem"
date: 2007-07-20
forum: General Help
---

### Post by Archoniam on 2007-07-20
I know how to install tarballs, and YES i know the link to 'How to install ANYTHING IN UBUNTU!'. Either every tarball i've installed is corrupt, or i'm doing something wrong. Let me use the package 'gnome-video-arcade-0.3.0' as an example. This is the ENTIRE process that i use according to the [ubuntu installation link]("http://monkeyblog.org/ubuntu/installing/#source") seen at that link.

```
archoniam@claptop:~$ sudo ./configure
sudo: ./configure: command not found
archoniam@claptop:~$ cd '/home/archoniam/gnome-video-arcade-0.3.0' 
archoniam@claptop:~/gnome-video-arcade-0.3.0$ ./configure
checking for a BSD-compatible install... /usr/bin/install -c
checking whether build environment is sane... yes
checking for gawk... no
checking for mawk... mawk
checking whether make sets $(MAKE)... yes
checking whether to enable maintainer-specific portions of Makefiles... no
checking for pkg-config... /usr/bin/pkg-config
checking pkg-config is at least version 0.9.0... yes
checking for GLIB... configure: error: Package requirements (glib-2.0 >= 2.12) were not met:

No package 'glib-2.0' found

Consider adjusting the PKG_CONFIG_PATH environment variable if you
installed software in a non-standard prefix.

Alternatively, you may set the environment variables GLIB_CFLAGS
and GLIB_LIBS to avoid the need to call pkg-config.
See the pkg-config man page for more details.

archoniam@claptop:~/gnome-video-arcade-0.3.0$ pkg-config
Must specify package names on the command line
archoniam@claptop:~/gnome-video-arcade-0.3.0$ pkg-config glib-2.0
archoniam@claptop:~/gnome-video-arcade-0.3.0$ sudo su
root@claptop:/home/archoniam/gnome-video-arcade-0.3.0# ./config
bash: ./config: No such file or directory
root@claptop:/home/archoniam/gnome-video-arcade-0.3.0# ./configure
checking for a BSD-compatible install... /usr/bin/install -c
checking whether build environment is sane... yes
checking for gawk... no
checking for mawk... mawk
checking whether make sets $(MAKE)... yes
checking whether to enable maintainer-specific portions of Makefiles... no
checking for pkg-config... /usr/bin/pkg-config
checking pkg-config is at least version 0.9.0... yes
checking for GLIB... configure: error: Package requirements (glib-2.0 >= 2.12) were not met:

No package 'glib-2.0' found

Consider adjusting the PKG_CONFIG_PATH environment variable if you
installed software in a non-standard prefix.

Alternatively, you may set the environment variables GLIB_CFLAGS
and GLIB_LIBS to avoid the need to call pkg-config.
See the pkg-config man page for more details.

root@claptop:/home/archoniam/gnome-video-arcade-0.3.0# 

```
Yeah i know, that first command i put in was just stupid/impatient at the time. Can anyone help me?

---

### Post by aysiu on 2007-07-20
Maybe something like ```
sudo apt-get install libglib2.0-dev
``` might help?

---

### Post by Archoniam on 2007-07-20
...Oh. :lol: Let's see if it works now. Well #$@%, i need the CDrom and the CD is not working for some reason. Lemme go find a disk mounter. I'll be back with an edit to see if it works.

---

### Post by aysiu on 2007-07-20
Why do you need the CD-ROM?

---

### Post by Archoniam on 2007-07-20
It says it's installing three packages. And, just as well, i had the same error, only the package not found was 'gtk+-2.0'! God, either something is going reeeally wrong with my ubuntu or i'm just missing eight million packages or something.

---

### Post by Archoniam on 2007-07-20
...Whoa, i just searched my aptitude and i'm missing a load of required -devs!

---

### Post by Archoniam on 2007-07-20
:shock: [SIZE="3"]Omgz. Still no frigging tar installation. Anyone know what's going on?[/SIZE][SIZE="2"]Aysiu?[/SIZE][SIZE="2"]Mods?[/SIZE][SIZE="1"]Forum members?[/SIZE]

---

### Post by aysiu on 2007-07-20
Post the error messages, just as you did in the first post.

---

### Post by Bablefish on 2007-07-20
It's like using Alien for me I just can't get that to work either. I just don't install tarballs  like you I can't install them I even tried some of those complier programs found in Add/Remove they don't work for me either. I just install precomplied programs such as those found on http:// [www.getdeb.net](www.getdeb.net) , but also recently I found a search tip  which you could use on any search engine that will lead you to a terminal install of practically any program you want as long as it is availible. "name of program debian install" I found that while looking for .deb file of Realplayer which I know I downloaded from a link on this forum which for now I can't find. But the command it lead me to helped another linux user install realplayer.

---

### Post by Archoniam on 2007-07-20
Mkay, sorry for making you wait so long. The error message, again:
```
archoniam@claptop:~$ cd '/home/archoniam/gnome-video-arcade-0.3.0' 
archoniam@claptop:~/gnome-video-arcade-0.3.0$ ./configure
checking for a BSD-compatible install... /usr/bin/install -c
checking whether build environment is sane... yes
checking for gawk... gawk
checking whether make sets $(MAKE)... yes
checking whether to enable maintainer-specific portions of Makefiles... no
checking for pkg-config... /usr/bin/pkg-config
checking pkg-config is at least version 0.9.0... yes
checking for GLIB... yes
checking for GTK... yes
checking for GCONF... yes
checking for GLADE... yes
checking for SQLITE... configure: error: Package requirements (sqlite3 >= 3.0.0) were not met:

No package 'sqlite3' found

Consider adjusting the PKG_CONFIG_PATH environment variable if you
installed software in a non-standard prefix.

Alternatively, you may set the environment variables SQLITE_CFLAGS
and SQLITE_LIBS to avoid the need to call pkg-config.
See the pkg-config man page for more details.

archoniam@claptop:~/gnome-video-arcade-0.3.0$ sudo apt-get install sqlite3
Password:
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Suggested packages:
  sqlite3-doc
The following NEW packages will be installed:
  sqlite3
0 upgraded, 1 newly installed, 0 to remove and 0 not upgraded.
Need to get 22.4kB of archives.
After unpacking 86.0kB of additional disk space will be used.
Get:1 http://us.archive.ubuntu.com feisty/universe sqlite3 3.3.13-0ubuntu1 [22.4kB]
Fetched 22.4kB in 2s (10.9kB/s)
Selecting previously deselected package sqlite3.
(Reading database ... 144520 files and directories currently installed.)
Unpacking sqlite3 (from .../sqlite3_3.3.13-0ubuntu1_i386.deb) ...
Setting up sqlite3 (3.3.13-0ubuntu1) ...
archoniam@claptop:~/gnome-video-arcade-0.3.0$ sudo apt-get install sqlite3-dev
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package sqlite3-dev
archoniam@claptop:~/gnome-video-arcade-0.3.0$ ./configure
checking for a BSD-compatible install... /usr/bin/install -c
checking whether build environment is sane... yes
checking for gawk... gawk
checking whether make sets $(MAKE)... yes
checking whether to enable maintainer-specific portions of Makefiles... no
checking for pkg-config... /usr/bin/pkg-config
checking pkg-config is at least version 0.9.0... yes
checking for GLIB... yes
checking for GTK... yes
checking for GCONF... yes
checking for GLADE... yes
checking for SQLITE... configure: error: Package requirements (sqlite3 >= 3.0.0) were not met:

No package 'sqlite3' found

Consider adjusting the PKG_CONFIG_PATH environment variable if you
installed software in a non-standard prefix.

Alternatively, you may set the environment variables SQLITE_CFLAGS
and SQLITE_LIBS to avoid the need to call pkg-config.
See the pkg-config man page for more details.

archoniam@claptop:~/gnome-video-arcade-0.3.0$ 


```
Kinda sucks, dosen't it?:lolflag:

---

### Post by RedSquirrel on 2007-07-20
The package is libsqlite3-dev. I would recommend using Synaptic or 'apt-cache search *search_terms*' to search for packages. The package name is important. ;)

---

### Post by Archoniam on 2007-07-21
(Error after error, i hate it man.)
Hey, i actually got it running! Thanks guys!!

---

### Post by aysiu on 2007-07-21
> **Archoniam said:**
> (Error after error, i hate it man.)
Hey, i actually got it running! Thanks guys!!
Care to share how you did (in case someone with the same problem stumbles upon this thread)?

---

