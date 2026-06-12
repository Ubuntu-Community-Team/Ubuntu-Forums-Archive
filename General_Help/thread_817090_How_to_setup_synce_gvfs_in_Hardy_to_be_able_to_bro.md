---
title: "How to setup synce gvfs in Hardy to be able to browse WM in Hardy"
date: 2008-06-03
forum: General Help
---

### Post by harty83 on 2008-06-03
As most know, Nautilus now uses gvfs rather than gnome-vfs thus synce-gnome will not work in Hardy.  So, Mark Ellis graciously created synge-gvfs which will allow us to browse our windows mobile devices via Nautilus.  Here are some instructions I found written by him with some slight changes by me:


1)  Follow instructions at [http://www.synce.org/moin/SynceWithUbuntu]("http://www.synce.org/moin/SynceWithUbuntu") to install synce and test basic functionality.  Note that you can install synce-hal rather than odccm if you want.

2) Make sure you have deb-src lines in /etc/apt/sources.list for your main repository. These should be exactly the same as the normal lines, but begin deb-src instead of just deb.

Also add this to sources.list, to get the source package from [Mark's] repository
```
deb-src [http://www.mpellis.org.uk/debian/](http://www.mpellis.org.uk/debian/) unstable main
```

3) Do an update

```
apt-get update
```

4) Get and build the gvfs source, note do not make install

```
apt-get source gvfs
cd gvfs-0.2.4
./configure
make

```

5) Install the following packages

```
sudo apt-get install libgvfscommon-dev gvfs-bin gvfs-backends dpkg-dev fakeroot cdbs librra-dev
```

6) Get and build synce-gvfs source

```
apt-get source synce-gvfs
```

which pulls [Marks] source package. There is a binary package for amd64 machines in the repo [see [http://www.mpellis.org.uk]](http://www.mpellis.org.uk])  if that's useful to anyone.

7)  In the new synce-gvfs dir, edit the rules file in the debian dir, and change /home/mark/sources/synce/gvfs/gvfs-0.2.2 to the absolute path of where your gvfs source tree is (/the/absolute/path/to/gvfs-0.2.4)


8)  Run ```
sudo dpkg-buildpackage -rfakeroot
``` from within the root of synce-gvfs directory (not the debian/ folder).

9)  If all goes well, in the dir one level up you now have a synce-gvfs deb which you can install with dpkg.
```
sudo dpkg -i ../synce-gvfs_0.1.svn20080423-1_i386.deb
```

10) Restart your computer.

I used this to set up both my amd64 and x86 machines.  I can browse, delete, edit, add files to both my WM5 and WM6 pocket pcs.

---

### Post by excogitation on 2008-07-19
Would you mind putting your deb online?

I just tried to follow your steps
which seemed to be working fine (apart librapi2..>=..)
but now I'm getting an error I can't resolve.

> In file included from gvfsbackendsynce.c:27:
/usr/include/rapi.h:852: error: expected ‘)’ before ‘lpDirectoryName’
gvfsbackendsynce.c:128: error: ‘ERROR_TOO_MANY_OPEN_FILES’ undeclared here (not in a function)
gvfsbackendsynce.c:129: error: ‘ERROR_NO_MORE_FILES’ undeclared here (not in a function)
gvfsbackendsynce.c:130: error: ‘ERROR_DISK_FULL’ undeclared here (not in a function)
make[3]: *** [gvfsd_synce-gvfsbackendsynce.o] Error 1
make[3]: Leaving directory `/home/excogitation/Desktop/ov_9650/synce-gvfs-0.1.svn20080423/daemon'
make[2]: *** [all-recursive] Error 1
make[2]: Leaving directory `/home/excogitation/Desktop/ov_9650/synce-gvfs-0.1.svn20080423'
make[1]: *** [all] Error 2
make[1]: Leaving directory `/home/excogitation/Desktop/ov_9650/synce-gvfs-0.1.svn20080423'
make: *** [debian/stamp-makefile-build] Error 2

I got the gvfs* debs though =D>

---

### Post by FoGia on 2008-07-24
Same problem here!

---

### Post by ayllu on 2008-07-28
I have the same problem in the 8 step. Are you shure that the directory is rithg

---

### Post by ayllu on 2008-07-31
I solved it. I follow the setps at [www.synce.com](www.synce.com) and, i removed gnomevfs from synaptic and istalled gvfs and its works. Just removing the gnomevfs old file and that its.

---

### Post by tkrewinkel on 2008-08-02
For me the same, many sides visited and no success. Decided to try this and indeed followed the instruction for installing synce and then removed synce-gnomevfs via synaptic. Installed gvfs simple via apt-get install gvfs restarted the computer and all worked just perfectly, many many thanks

---

### Post by xiaoyong on 2008-08-10
I got errors when I followed to 8 step.

```

```
dpkg-source: warning: Version number suggests Ubuntu changes, but Maintainer: does not have Ubuntu address
dpkg-source: warning: Version number suggests Ubuntu changes, but there is no XSBC-Original-Maintainer field
dpkg-source: building gvfs using existing gvfs_0.2.5.orig.tar.gz
dpkg-source: building gvfs in gvfs_0.2.5-0ubuntu2.diff.gz
dpkg-source: cannot represent change to synce-gvfs_0.1.svn20080423.orig.tar.gz: binary file contents changed
dpkg-source: cannot represent change to synce-gvfs_0.1.svn20080423-1.diff.gz: binary file contents changed
dpkg-source: warning: executable mode 0755 of 'synce-gvfs-0.1.svn20080423/install-sh' will not be represented in diff
dpkg-source: warning: executable mode 0755 of 'synce-gvfs-0.1.svn20080423/config.sub' will not be represented in diff
dpkg-source: warning: executable mode 0755 of 'synce-gvfs-0.1.svn20080423/compile' will not be represented in diff
dpkg-source: cannot represent change to synce-gvfs-0.1.svn20080423/pixmaps/synce-gvfs.png: binary file contents changed
dpkg-source: warning: newly created empty file 'synce-gvfs-0.1.svn20080423/NEWS' will not be represented in diff
dpkg-source: warning: executable mode 0755 of 'synce-gvfs-0.1.svn20080423/config.guess' will not be represented in diff
dpkg-source: warning: executable mode 0755 of 'synce-gvfs-0.1.svn20080423/autogen.sh' will not be represented in diff
dpkg-source: warning: executable mode 0755 of 'synce-gvfs-0.1.svn20080423/mkinstalldirs' will not be represented in diff
dpkg-source: warning: executable mode 0755 of 'synce-gvfs-0.1.svn20080423/depcomp' will not be represented in diff
dpkg-source: warning: executable mode 0755 of 'synce-gvfs-0.1.svn20080423/configure' will not be represented in diff
dpkg-source: warning: executable mode 0755 of 'synce-gvfs-0.1.svn20080423/missing' will not be represented in diff
dpkg-source: warning: executable mode 0755 of 'synce-gvfs-0.1.svn20080423/debian/rules' will not be represented in diff
dpkg-source: warning: ignoring deletion of file hal/hal-marshal.c
dpkg-source: warning: ignoring deletion of file hal/hal-marshal.h
dpkg-source: building gvfs in gvfs_0.2.5-0ubuntu2.dsc
dpkg-source: unrepresentable changes to source
dpkg-buildpackage: failure: dpkg-source -b gvfs-0.2.5 gave error exit status 1
```

```

Why?

---

### Post by harty83 on 2008-08-10
Packages are now in the following repositories.

Add the following to /etc/apt/sources.list
```

deb http://ppa.launchpad.net/synce/ubuntu hardy main
deb-src http://ppa.launchpad.net/synce/ubuntu hardy main

```

then 

```
sudo apt-get update
```

then 

```
sudo apt-get install synce-gvfs
```

---

### Post by excogitation on 2008-08-11
Now if I just hadn't tried to install network-manager 0.7 ... I might not have upgraded to Intrepid already :-\"

Anyways on Intrepid it doesn't work
> #
/usr/lib/synce-gvfs/gvfsd-synce
#
Added new job source 0x897b818 (GVfsBackendSynce)
#
Queued new job 0x897b858 (GVfsJobMount)
#
send_reply, failed: 0
#
register_mount_callback, mount_reply: (nil), error: 0x8979850
#
Mount failed: DBus error org.freedesktop.DBus.Error.InvalidArgs: Argument 5 is specified to be of type "s", but is actually of type "b"

---

### Post by Karolis on 2008-08-16
Sorry for a stupid question, but I have followed both tutorials (installing synce and then installing synce-gvfs) and everything went just fine, but how do I access my phone now?

If I run synce-pls in terminal, it shows the files on my device, but how do I see those files in Nautilus?

---

### Post by harty83 on 2008-08-16
> **Karolis said:**
> Sorry for a stupid question, but I have followed both tutorials (installing synce and then installing synce-gvfs) and everything went just fine, but how do I access my phone now?

If I run synce-pls in terminal, it shows the files on my device, but how do I see those files in Nautilus?

Type in synce:/// in nautilus address bar.

Or you install synce-trayicon

```
sudo apt-get install synce-trayicon
```

Open it or add it to your startup services 
```
synce-trayicon
```

Right click on the icon in your notification tray and click on preferences.  Select how you are communicating with the device.

---

### Post by excogitation on 2008-08-17
should have checked if it has already been answered first :-)

---

### Post by majedaly on 2011-09-05
> **harty83 said:**
> Packages are now in the following repositories.

Add the following to /etc/apt/sources.list
```

deb http://ppa.launchpad.net/synce/ubuntu hardy main
deb-src http://ppa.launchpad.net/synce/ubuntu hardy main

```then 

```
sudo apt-get update
```then 

```
sudo apt-get install synce-gvfs
```
 
Thanks, that worked perfectly on Maverick, may be you want to update your first post?

---

