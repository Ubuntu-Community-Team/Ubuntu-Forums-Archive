---
title: "MP3/gstreamer problems"
date: 2006-08-27
forum: General Help
---

### Post by Andrew07 on 2006-08-27
Okay, this morning I decided to try and install XGL. It failed, ended up having to re-install Ubuntu. Tried again a few hours ago, and it worked without a hitch. Now though, I need to get my mp3 playback abilities back.

I went to the restricted formats page, followed the directions, but when I try to install the gstreamer0.10-plugins-ugly package, it gives me this error:

Error: Dependency is not satisfiable: libc6

I mentioned I installed XGL, because I'm guessing that it might be the reason why. Anyway I can do this?

---

### Post by croak77 on 2006-08-28
Try installing libc6. Then gstreamer0.10-plugins-ugly. Maybe the server was updating or something.

---

### Post by Andrew07 on 2006-08-28
Tried to re-install libc6, but still nothing. Same error as before.

---

### Post by Andrew07 on 2006-08-28
Also, incase it matters. I have NTFS-3g packaged on this computer also, if that has any effect at all.

---

### Post by givré on 2006-08-29
libc6 dependency are in the majority of the case due to a mix between package of different release. Let's see your /etc/apt/sources.list

---

### Post by Andrew07 on 2006-08-29
Can do. Here it is: 

> deb-src [http://au.archive.ubuntu.com/ubuntu/](http://au.archive.ubuntu.com/ubuntu/) dapper main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://au.archive.ubuntu.com/ubuntu/](http://au.archive.ubuntu.com/ubuntu/) dapper-updates main restricted
deb-src [http://au.archive.ubuntu.com/ubuntu/](http://au.archive.ubuntu.com/ubuntu/) dapper-updates main restricted

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) dapper universe main restricted multiverse
# deb-src [http://au.archive.ubuntu.com/ubuntu/](http://au.archive.ubuntu.com/ubuntu/) dapper universe

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb [http://au.archive.ubuntu.com/ubuntu/](http://au.archive.ubuntu.com/ubuntu/) dapper-backports main restricted universe multiverse
# deb-src [http://au.archive.ubuntu.com/ubuntu/](http://au.archive.ubuntu.com/ubuntu/) dapper-backports main restricted universe multiverse

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security main restricted
# deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security universe
# deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security universe
deb [http://www.beerorkid.com/compiz](http://www.beerorkid.com/compiz) dapper main
deb [http://ubuntu.compiz.net/](http://ubuntu.compiz.net/) dapper main
deb [http://givre.cabspace.com/ubuntu/](http://givre.cabspace.com/ubuntu/) dapper main
deb-src [http://givre.cabspace.com/ubuntu/](http://givre.cabspace.com/ubuntu/) dapper main
deb [http://wine.sourceforge.net/apt/](http://wine.sourceforge.net/apt/) binary/

Also, goodjob on the NTFS-3g guide. It worked fine without any problems.

---

### Post by givré on 2006-08-29
ok, so the problem seems to not be there.
Let see the version of the package you have :
Search for libc6 in synaptic and have a look at the version, it should be : 2.3.6-0ubuntu20
have a look also at the version of gstreammer, it should be 0.10.4-0ubuntu1.
You can then look at the version of libc6 needed with right-click> proprity tab dependencie.

---

### Post by Andrew07 on 2006-08-29
My version of libc6 is 2.3.6-OUbuntu20. As for gstreamer, I don't see any package that is labeled just "gstreamer." gstreamer0.10-alsa is version 0.10.7-Oubuntu5 and gstreamer0.10-esd is version 0.10.3-Oubunutu4.

---

### Post by givré on 2006-08-29
The result of that should be enough :
```
aptitude show gstreamer0.10-plugins-ugly
```

---

### Post by Andrew07 on 2006-08-29
Here is the result:

> Package: gstreamer0.10-plugins-ugly
State: not installed
Version: 0.10.3-0ubuntu3
Priority: optional
Section: universe/libs
Maintainer: Maintainers of GStreamer packages <pkg-gstreamer-maintainers@lists.alioth.debian.org>
Uncompressed Size: 496k
Depends: liba52-0.7.4, libc6 (>= 2.3.4-1), libdvdread3, libgcc1 (>= 1:4.0.2),
         libglib2.0-0 (>= 2.10.0), libgstreamer-plugins-base0.10-0 (>= 0.10.7),
         libgstreamer0.10-0 (>= 0.10.6), libid3tag0 (>= 0.15.1b), libmad0 (>=
         0.15.1b), libmpeg2-4, liboil0.3 (>= 0.3.6), libsidplay1, libxml2 (>=
         2.6.24), zlib1g (>= 1:1.2.1)
Description: GStreamer plugins from the "ugly" set
 GStreamer is a streaming media framework, based on graphs of filters which
 operate on media data.  Applications using this library can do anything from
 real-time sound processing to playing videos, and just about anything else
 media-related.  Its plugin-based architecture means that new data types or
 processing capabilities can be added simply by installing new plug-ins.

 This packages contains plugins from the "ugly" set, a set of good-quality
 plug-ins that might pose distribution problems.

---

### Post by givré on 2006-08-29
```
libc6 (>= 2.3.4-1),
```So there should be no problem. What do 
you have when you do :
```
sudo apt-get install gstreamer0.10-plugins-ugly
```

---

