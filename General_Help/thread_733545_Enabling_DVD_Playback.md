---
title: "Enabling DVD Playback"
date: 2008-03-23
forum: General Help
---

### Post by grjemo on 2008-03-23
I am relatively new to Ubuntu.  I was using the 32 bit version for a while, and after messing around in my BIOS, I realized I had 64 bit support.  Everything has gone smoothly, until I tried to enable DVD playback.

First, into the terminal, I entered:

*sudo apt-get install libdvdread3*

No problems here. Then:
[I]
sudo /usr/share/doc/libdvdread3/install-css.sh[/I]

What I got was:
[I]
No prebuilt binary available.  Will try to build and install it.
You need to have debhelper and fakeroot installed.
If not, interrupt now, install them and rerun this script.

This is higly experimental, look out for what happens below.
If you want to stop, interrupt now (control-c), else press
return to proceed[/I]

I installed debhelper and fakeroot, tried again, hit enter and got this:

No prebuilt binary available.  Will try to build and install it.
You need to have debhelper and fakeroot installed.
If not, interrupt now, install them and rerun this script.

This is higly experimental, look out for what happens below.
If you want to stop, interrupt now (control-c), else press
return to proceed

[I]--22:58:27--  [http://www.dtek.chalmers.se/groups/dvd/deb/libdvdcss_1.2.5.orig.tar.gz](http://www.dtek.chalmers.se/groups/dvd/deb/libdvdcss_1.2.5.orig.tar.gz)
           => `libdvdcss_1.2.5.orig.tar.gz'
Resolving [www.dtek.chalmers.se](www.dtek.chalmers.se)... 129.16.30.198
Connecting to www.dtek.chalmers.se|129.16.30.198|:80... connected.
HTTP request sent, awaiting response... 200 OK
Length: 267,699 (261K) [application/x-tar]

100%[====================================>] 267,699      272.36K/s             

22:58:29 (271.33 KB/s) - `libdvdcss_1.2.5.orig.tar.gz' saved [267699/267699]

--22:58:29--  [http://www.dtek.chalmers.se/groups/dvd/deb/libdvdcss_1.2.5-1.diff.gz](http://www.dtek.chalmers.se/groups/dvd/deb/libdvdcss_1.2.5-1.diff.gz)
           => `libdvdcss_1.2.5-1.diff.gz'
Resolving [www.dtek.chalmers.se](www.dtek.chalmers.se)... 129.16.30.198
Connecting to www.dtek.chalmers.se|129.16.30.198|:80... connected.
HTTP request sent, awaiting response... 200 OK
Length: 20 [text/plain]

100%[====================================>] 20            --.--K/s             

22:58:29 (2.51 MB/s) - `libdvdcss_1.2.5-1.diff.gz' saved [20/20]

--22:58:29--  [http://www.dtek.chalmers.se/groups/dvd/deb/libdvdcss_1.2.5-1.dsc](http://www.dtek.chalmers.se/groups/dvd/deb/libdvdcss_1.2.5-1.dsc)
           => `libdvdcss_1.2.5-1.dsc'
Resolving [www.dtek.chalmers.se](www.dtek.chalmers.se)... 129.16.30.198
Connecting to www.dtek.chalmers.se|129.16.30.198|:80... connected.
HTTP request sent, awaiting response... 200 OK
Length: 341 [text/plain]

100%[====================================>] 341           --.--K/s             

22:58:29 (44.88 MB/s) - `libdvdcss_1.2.5-1.dsc' saved [341/341]

dpkg-source: warning: extracting unsigned source package (./libdvdcss_1.2.5-1.dsc)
dpkg-source: extracting libdvdcss in libdvdcss-1.2.5
dpkg-source: unpacking libdvdcss_1.2.5.orig.tar.gz
dpkg-source: applying ./libdvdcss_1.2.5-1.diff.gz
dh_testdir
./configure --prefix=/usr --mandir=${prefix}/share/man \
                --infodir=${prefix}/share/info
checking build system type... x86_64-unknown-linux-gnu
checking host system type... x86_64-unknown-linux-gnu
checking target system type... x86_64-unknown-linux-gnu
checking for a BSD-compatible install... /usr/bin/install -c
checking whether build environment is sane... yes
checking for gawk... no
checking for mawk... mawk
checking whether make sets $(MAKE)... yes
checking for gcc... gcc
checking for C compiler default output... configure: error: C compiler cannot create executables
See `config.log' for more details.
make: *** [build-stamp] Error 77[/I]

Can anyone help me?

---

### Post by ameba on 2008-03-23
this all you need to play dvds

---

### Post by ericartman on 2008-03-24
I highly recommend and use this
[http://ubuntuforums.org/showthread.php?p=3774207#post3774207](http://ubuntuforums.org/showthread.php?p=3774207#post3774207)

check it out.

Cart

---

### Post by grjemo on 2008-03-24
Thanks, that worked perfectly.

---

