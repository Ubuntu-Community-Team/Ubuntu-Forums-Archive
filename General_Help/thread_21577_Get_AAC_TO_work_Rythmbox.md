---
title: "Get AAC TO work Rythmbox"
date: 2005-03-22
forum: General Help
---

### Post by ChaperonNoir on 2005-03-22
I use Rythmbox for my music needs.

I have a huge library of mpeg4 audio files ( AAC).

How do i get the proper plugin ?

---

### Post by bored2k on 2005-03-22
[QUOTE=ChaperonNoir]I use Rythmbox for my music needs.

I have a huge library of mpeg4 audio files ( AAC).

How do i get the proper plugin ?[/QUOTE]
 [http://ubuntuguide.org/#codecs](http://ubuntuguide.org/#codecs)

deb [http://luca.pca.it/debian/](http://luca.pca.it/debian/) ./
--> gstreamer-faad

---

### Post by ChaperonNoir on 2005-03-23
[QUOTE=bored2k][http://ubuntuguide.org/#codecs](http://ubuntuguide.org/#codecs)

deb [http://luca.pca.it/debian/](http://luca.pca.it/debian/) ./
--> gstreamer-faad[/QUOTE]

Thanx i understand what i need to do.

```
deb cdrom:[Ubuntu 5.04 _Hoary Hedgehog_ - Alpha amd64 Binary-1 (20050217)]/ unstable main restricted


## Uncomment the following two lines to fetch updated software from the network
deb http://ca.archive.ubuntu.com/ubuntu hoary main restricted
deb-src http://ca.archive.ubuntu.com/ubuntu hoary main restricted

## Uncomment the following two lines to fetch major bug fix updates produced
## after the final release of the distribution.
#deb http://ca.archive.ubuntu.com/ubuntu hoary-updates main restricted
#deb-src http://ca.archive.ubuntu.com/ubuntu hoary-updates main restricted

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb http://ca.archive.ubuntu.com/ubuntu hoary universe
deb-src http://ca.archive.ubuntu.com/ubuntu hoary universe

deb http://security.ubuntu.com/ubuntu hoary-security main restricted
deb-src http://security.ubuntu.com/ubuntu hoary-security main restricted

deb http://security.ubuntu.com/ubuntu hoary-security universe
deb-src http://security.ubuntu.com/ubuntu hoary-security universe

[B]deb http://luca.pca.it/debian/ ./
deb-src http://luca.pca.it/debian/ ./[/B]
``` 

After this, 

sudo apt-get update

```
Ign cdrom://Ubuntu 5.04 _Hoary Hedgehog_ - Alpha amd64 Binary-1 (20050217) unstable Release.gpg
Get:1 http://security.ubuntu.com hoary-security Release.gpg [189B]
Ign http://luca.pca.it ./ Release.gpg
Get:2 http://security.ubuntu.com hoary-security Release [16.9kB]
Ign http://luca.pca.it ./ Release
Hit http://security.ubuntu.com hoary-security/main Packages
Ign http://luca.pca.it ./ Packages
Hit http://security.ubuntu.com hoary-security/restricted Packages
Hit http://security.ubuntu.com hoary-security/main Sources
Hit http://security.ubuntu.com hoary-security/restricted Sources
Get:3 http://security.ubuntu.com hoary-security/universe Packages [14B]
Get:4 http://security.ubuntu.com hoary-security/universe Sources [14B]
[B]Ign http://luca.pca.it ./ Sources
Hit http://luca.pca.it ./ Packages[/B]
Get:5 http://luca.pca.it ./ Sources [2537B]
Get:6 http://ca.archive.ubuntu.com hoary Release.gpg [189B]
Get:7 http://ca.archive.ubuntu.com hoary Release [19.9kB]
Get:8 http://ca.archive.ubuntu.com hoary/main Packages [481kB]
Hit http://ca.archive.ubuntu.com hoary/restricted Packages
Get:9 http://ca.archive.ubuntu.com hoary/main Sources [174kB]
Hit http://ca.archive.ubuntu.com hoary/restricted Sources
Get:10 http://ca.archive.ubuntu.com hoary/universe Packages [2054kB]
Hit http://ca.archive.ubuntu.com hoary/universe Sources
Fetched 2749kB in 12s (214kB/s)
Reading Package Lists... Done
**root@amd64:/home/edmond # apt-get install gstreamer-faad**
Reading Package Lists... Done
Building Dependency Tree... Done
E: Couldn't find package gstreamer-faad
[B]root@amd64:/home/edmond # apt-cache search faad
root@amd64:/home/edmond # apt-get install gstreamer0.8-faad[/B]
Reading Package Lists... Done
Building Dependency Tree... Done
E: Couldn't find package gstreamer0.8-faad
```

---

### Post by ChaperonNoir on 2005-03-24
I'm going to have them i think


What i did

apt-get source --compile gstreamer0.8-faad

It got the source everything but the compilation failed :(

I need to compile it myself.

The ./configure make sudo make install doesnt work :0

Im not really a compilation expert... i never succeeded compiling something .

Helps :P

---

### Post by ChaperonNoir on 2005-03-24
```
root@amd64:/etc/apt # apt-get source --compile  gstreamer0.8-faad
Reading Package Lists... Done
Building Dependency Tree... Done
Need to get 4138kB of source archives.
Get:1 [http://luca.pca.it](http://luca.pca.it) ./ gst-plugins0.8 0.8.7-3.gismo (dsc) [856B]
Get:2 [http://luca.pca.it](http://luca.pca.it) ./ gst-plugins0.8 0.8.7-3.gismo (tar) [4089kB]
Get:3 [http://luca.pca.it](http://luca.pca.it) ./ gst-plugins0.8 0.8.7-3.gismo (diff) [48.6kB]
Fetched 3B in 1s (3B/s)
Skipping unpack of already unpacked source in gst-plugins0.8-0.8.7
dpkg-buildpackage: source package is gst-plugins0.8
dpkg-buildpackage: source version is 0.8.7-3.gismo
dpkg-buildpackage: source maintainer is Luca Capello <luca@pca.it>
dpkg-buildpackage: host architecture is amd64
dpkg-checkbuilddeps: Unmet build dependencies: libgstreamer0.8-dev (>= 0.8.7.1) autotools-dev cdbs (>= 0.4.20) libgconf2-dev (>= 2.4) libglib2.0-dev (>= 2.2.0) libxml2-dev (>= 2.4.23) zlib1g-dev (>= 1:1.1.4) libfaad2-dev (>= 2.0) liblame-dev (>= 3.91)
dpkg-buildpackage: Build dependencies/conflicts unsatisfied; aborting.
dpkg-buildpackage: (Use -d flag to override.)
Build command ‘cd gst-plugins0.8-0.8.7 && dpkg-buildpackage -b -uc’ failed.
E: Child process failed
root@amd64:/etc/apt #
```

---

### Post by ChaperonNoir on 2005-03-24
Lots of views but no replies ;( cmon guys im so close.

---

### Post by attempted_user on 2005-03-26
From the looks of your dpkg output, it seems that the only problem is that it's missing a library package it needs. Try this:

```
apt-get install libgstreamer0.8-dev
``` 

If apt complains that it can't find the package, you can download it directly from [the debian package archive](http://packages.debian.org/testing/libdevel/libgstreamer0.8-dev)  and use ```
dpkg -i libgstreamer0.8-dev_0.8.9-2_i386.deb
```

good luck.

---

