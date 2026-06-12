---
title: "How can I easily remove these hundreds of packages?"
date: 2015-09-29
forum: General Help
---

### Post by herculeesjr on 2015-09-29
So I was in a rush about to leave for work and needed a program to burn flac files to a music cd, in a rush I saw someone recommend "k3b" and without checking dependencies I installed it. Oh my god this must be the worst designed program ever it might as well depend on every package ever invented. Anyways... I went to remove it and find that apt-get autoremove removed less than ten packages so I dig around the internet to see if I can find an install history and I did, I found this:
```
libkde3support4:amd64 (4.14.10-3, automatic), k3b-data:amd64 (2.0.2-8, automatic), libresid-builder0c2a:amd64 (2.1.1-14, automatic), libxkbcommon-x11-0:amd64 (0.5.0-1, automatic), ntrack-module-libnl-0:amd64 (016-1.3, automatic), libhunspell-1.3-0:amd64 (1.3.3-3+b1, automatic), emacsen-common:amd64 (2.0.8, automatic), libmatroska6v5:amd64 (1.4.2-4, automatic), libwinpr-thread0.1:amd64 (1.1.0~git20140921.1.440916e+dfsg1-5, automatic), libkrosscore4:amd64 (4.14.10-3, automatic), oxygen-icon-theme:amd64 (4.14.0-1, automatic), libktexteditor4:amd64 (4.14.10-3, automatic), kdelibs5-data:amd64 (4.14.10-3, automatic), libkdeui5:amd64 (4.14.10-3, automatic), libkdeclarative5:amd64 (4.14.10-3, automatic), libfam0:amd64 (2.7.0-17.1+b1, automatic), libthreadweaver4:amd64 (4.14.10-3, automatic), libfreerdp-client1.1:amd64 (1.1.0~git20140921.1.440916e+dfsg1-5, automatic), libvorbisfile3:amd64 (1.3.4-2, automatic), libwinpr-utils0.1:amd64 (1.1.0~git20140921.1.440916e+dfsg1-5, automatic), libfreerdp-core1.1:amd64 (1.1.0~git20140921.1.440916e+dfsg1-5, automatic), libxcb-render-util0:amd64 (0.3.9-1, automatic), kde-runtime:amd64 (15.08.1-1, automatic), libchromaprint0:amd64 (1.2-1+b1, automatic), libwinpr-synch0.1:amd64 (1.1.0~git20140921.1.440916e+dfsg1-5, automatic), libkparts4:amd64 (4.14.10-3, automatic), aspell:amd64 (0.60.7~20110707-3, automatic), libqt4-sql:amd64 (4.8.7+dfsg-3, automatic), libqca2:amd64 (2.1.0.3-4, automatic), libexiv2-14:amd64 (0.25-2, automatic), libntrack0:amd64 (016-1.3, automatic), kde-runtime-data:amd64 (15.08.1-1, automatic), libphonon4:amd64 (4.8.3-2, automatic), cdparanoia:amd64 (3.10.2+debian-11, automatic), libwinpr-pool0.1:amd64 (1.1.0~git20140921.1.440916e+dfsg1-5, automatic), libspeexdsp1:amd64 (1.2~rc1.2-1, automatic), libkemoticons4:amd64 (4.14.10-3, automatic), libaspell15:amd64 (0.60.7~20110707-3, automatic), cdrdao:amd64 (1.2.3-2+b1, automatic), libnepomukquery4a:amd64 (4.14.10-3, automatic), libsdl-image1.2:amd64 (1.2.12-5+b5, automatic), libpulse-mainloop-glib0:amd64 (6.0-5, automatic), libkmediaplayer4:amd64 (4.14.10-3, automatic), libkrb5-26-heimdal:amd64 (1.6~rc2+dfsg-10, automatic), libneon27-gnutls:amd64 (0.30.1-1, automatic), libwinpr-handle0.1:amd64 (1.1.0~git20140921.1.440916e+dfsg1-5, automatic), libwinpr-crt0.1:amd64 (1.1.0~git20140921.1.440916e+dfsg1-5, automatic), libroken18-heimdal:amd64 (1.6~rc2+dfsg-10, automatic), libvlccore8:amd64 (2.2.1-4, automatic), libqt4-qt3support:amd64 (4.8.7+dfsg-3, automatic), libkcddb4:amd64 (15.08.0-1, automatic), libfreerdp-cache1.1:amd64 (1.1.0~git20140921.1.440916e+dfsg1-5, automatic), libwinpr-interlocked0.1:amd64 (1.1.0~git20140921.1.440916e+dfsg1-5, automatic), libgif4:amd64 (4.1.6-11, automatic), katepart:amd64 (4.14.3-2, automatic), libcanberra0:amd64 (0.30-2.1, automatic), libqt4-svg:amd64 (4.8.7+dfsg-3, automatic), libproxy-tools:amd64 (0.4.11-4.2, automatic), libqt4-xmlpatterns:amd64 (4.8.7+dfsg-3, automatic), vlc-nox:amd64 (2.2.1-4, automatic), libopenexr6v5:amd64 (1.6.1-8.1+b2, automatic), libkdnssd4:amd64 (4.14.10-3, automatic), soprano-daemon:amd64 (2.9.4+dfsg-3+b1, automatic), libupnp6:amd64 (1.6.19+git20141001-1, automatic), phonon:amd64 (4.8.3-2, automatic), libqt4-opengl:amd64 (4.8.7+dfsg-3, automatic), libsoprano4:amd64 (2.9.4+dfsg-3+b1, automatic), libdbusmenu-qt2:amd64 (0.9.3+15.10.20150604-1, automatic), libwind0-heimdal:amd64 (1.6~rc2+dfsg-10, automatic), libkatepartinterfaces4:amd64 (4.14.3-2, automatic), wodim:amd64 (1.1.11-3, automatic), libebml4v5:amd64 (1.3.1-5, automatic), genisoimage:amd64 (1.1.11-3, automatic), udisks2:amd64 (2.1.6-2, automatic), libusageenvironment1:amd64 (2014.01.13-1, automatic), libxcb-image0:amd64 (0.4.0-1, automatic), libntdb1:amd64 (1.0-7, automatic), libxcb-xkb1:amd64 (1.10-3+b1, automatic), kdelibs5-plugins:amd64 (4.14.10-3, automatic), libhcrypto4-heimdal:amd64 (1.6~rc2+dfsg-10, automatic), libqtwebkit4:amd64 (2.3.4.dfsg-5, automatic), libqt4-script:amd64 (4.8.7+dfsg-3, automatic), libheimntlm0-heimdal:amd64 (1.6~rc2+dfsg-10, automatic), libxcb-xv0:amd64 (1.10-3+b1, automatic), libxcb-icccm4:amd64 (0.4.1-1, automatic), parted:amd64 (3.2-7, automatic), libkjsapi4:amd64 (4.14.10-3, automatic), libcddb2:amd64 (1.3.2-5, automatic), libpolkit-agent-1-0:amd64 (0.105-12, automatic), libbasicusageenvironment0:amd64 (2014.01.13-1, automatic), libkactivities6:amd64 (4.13.3-1, automatic), libfreerdp-codec1.1:amd64 (1.1.0~git20140921.1.440916e+dfsg1-5, automatic), libwinpr-input0.1:amd64 (1.1.0~git20140921.1.440916e+dfsg1-5, automatic), libgroupsock1:amd64 (2014.01.13-1, automatic), libiso9660-8:amd64 (0.83-4.2, automatic), libmagic1:amd64 (5.25-2, automatic), libk3b6:amd64 (2.0.2-8+b1, automatic), libqt5core5a:amd64 (5.4.2+dfsg-9, automatic), libfreerdp-gdi1.1:amd64 (1.1.0~git20140921.1.440916e+dfsg1-5, automatic), libparted2:amd64 (3.2-7, automatic), libflac++6v5:amd64 (1.3.1-4, automatic), libwinpr-heap0.1:amd64 (1.1.0~git20140921.1.440916e+dfsg1-5, automatic), libtevent0:amd64 (0.9.25-2, automatic), libxcb-keysyms1:amd64 (0.4.0-1, automatic), libenchant1c2a:amd64 (1.6.0-10.1, automatic), libao-common:amd64 (1.1.0-3, automatic), libkcompactdisc4:amd64 (15.04.3-1, automatic), libwinpr-rpc0.1:amd64 (1.1.0~git20140921.1.440916e+dfsg1-5, automatic), vlc-data:amd64 (2.2.1-4, automatic), libwinpr-library0.1:amd64 (1.1.0~git20140921.1.440916e+dfsg1-5, automatic), libutempter0:amd64 (1.1.6-1, automatic), libknewstuff3-4:amd64 (4.14.10-3, automatic), libnepomukutils4:amd64 (4.14.10-3, automatic), libfreerdp-locale1.1:amd64 (1.1.0~git20140921.1.440916e+dfsg1-5, automatic), libilmbase6v5:amd64 (1.0.1-6.2, automatic), libfreerdp-primitives1.1:amd64 (1.1.0~git20140921.1.440916e+dfsg1-5, automatic), liblircclient0:amd64 (0.9.0~pre1-1.2, automatic), kdoctools:amd64 (4.14.10-3, automatic), sgml-data:amd64 (2.0.10, automatic), libmtp9:amd64 (1.1.9-3, automatic), libgles2-mesa:amd64 (10.6.8-1, automatic), libldb1:amd64 (1.1.20-2, automatic), libkxmlrpcclient4:amd64 (4.14.10-1, automatic), libkpty4:amd64 (4.14.10-3, automatic), libpostproc-ffmpeg53:amd64 (2.7.2-2+b1, automatic), libasn1-8-heimdal:amd64 (1.6~rc2+dfsg-10, automatic), libkjsembed4:amd64 (4.14.10-3, automatic), libwinpr-registry0.1:amd64 (1.1.0~git20140921.1.440916e+dfsg1-5, automatic), libqt4-designer:amd64 (4.8.7+dfsg-3, automatic), libsolid4:amd64 (4.14.10-3, automatic), libkhtml5:amd64 (4.14.10-3, automatic), libswscale-ffmpeg3:amd64 (2.7.2-2+b1, automatic), dictionaries-common:amd64 (1.26.3, automatic), libntrack-qt4-1:amd64 (016-1.3, automatic), libclucene-core1v5:amd64 (2.3.3.4-4.1, automatic), libtdb1:amd64 (1.3.7-1, automatic), fonts-freefont-ttf:amd64 (20120503-4, automatic), libkfile4:amd64 (4.14.10-3, automatic), libwinpr-sspi0.1:amd64 (1.1.0~git20140921.1.440916e+dfsg1-5, automatic), samba-libs:amd64 (4.1.17+dfsg-4, automatic), phonon-backend-vlc:amd64 (0.8.2-1, automatic), libpython2.7:amd64 (2.7.10-4, automatic), libdvbpsi10:amd64 (1.3.0-2, automatic), libgles1-mesa:amd64 (10.6.8-1, automatic), libsdl1.2debian:amd64 (1.2.15-11, automatic), libqt5x11extras5:amd64 (5.4.2-2+b1, automatic), libatasmart4:amd64 (0.19-3, automatic), libattica0.4:amd64 (0.4.2-2, automatic), libkdesu5:amd64 (4.14.10-3, automatic), libdlrestrictions1:amd64 (0.15.19, automatic), libheimbase1-heimdal:amd64 (1.6~rc2+dfsg-10, automatic), libknotifyconfig4:amd64 (4.14.10-3, automatic), docbook-xml:amd64 (4.5-7.3, automatic), libqt5widgets5:amd64 (5.4.2+dfsg-9, automatic), libmusicbrainz5cc2v5:amd64 (5.1.0+git20150707-5, automatic), libxcb-composite0:amd64 (1.10-3+b1, automatic), libxcb-randr0:amd64 (1.10-3+b1, automatic), libfreerdp-common1.1.0:amd64 (1.1.0~git20140921.1.440916e+dfsg1-5, automatic), libkdecore5:amd64 (4.14.10-3, automatic), kdelibs-bin:amd64 (4.14.10-3, automatic), libfreerdp-crypto1.1:amd64 (1.1.0~git20140921.1.440916e+dfsg1-5, automatic), libtalloc2:amd64 (2.1.3-1, automatic), libva-x11-1:amd64 (1.6.1-1, automatic), libmtp-common:amd64 (1.1.9-3, automatic), plasma-scriptengine-javascript:amd64 (15.08.1-1, automatic), libnepomuk4:amd64 (4.14.10-3, automatic), libbsd0:amd64 (0.7.0-2, automatic), libwinpr-path0.1:amd64 (1.1.0~git20140921.1.440916e+dfsg1-5, automatic), libwinpr-dsparse0.1:amd64 (1.1.0~git20140921.1.440916e+dfsg1-5, automatic), vlc:amd64 (2.2.1-4, automatic), libvlc5:amd64 (2.2.1-4, automatic), libqt5dbus5:amd64 (5.4.2+dfsg-9, automatic), python-talloc:amd64 (2.1.3-1, automatic), docbook-xsl:amd64 (1.78.1+dfsg-1, automatic), libkntlm4:amd64 (4.14.10-3, automatic), libstreams0v5:amd64 (0.7.8-2+b1, automatic), libkdewebkit5:amd64 (4.14.10-3, automatic), libpcre16-3:amd64 (8.35-7.2, automatic), liblua5.2-0:amd64 (5.2.4-1, automatic), liblivemedia23:amd64 (2014.01.13-1, automatic), libvcdinfo0:amd64 (0.7.24+dfsg-0.2, automatic), libiodbc2:amd64 (3.52.9-2, automatic), libwinpr-sysinfo0.1:amd64 (1.1.0~git20140921.1.440916e+dfsg1-5, automatic), libkcmutils4:amd64 (4.14.10-3, automatic), k3b:amd64 (2.0.2-8+b1), libao4:amd64 (1.1.0-3, automatic), libpolkit-qt-1-1:amd64 (0.112.0-4, automatic), libsidplay2:amd64 (2.1.1-14, automatic), libwbclient0:amd64 (4.1.17+dfsg-4, automatic), libwinpr-environment0.1:amd64 (1.1.0~git20140921.1.440916e+dfsg1-5, automatic), libgssapi3-heimdal:amd64 (1.6~rc2+dfsg-10, automatic), libqt5gui5:amd64 (5.4.2+dfsg-9, automatic), aspell-en:amd64 (7.1-0-1.1, automatic), libstreamanalyzer0v5:amd64 (0.7.8-2+b1, automatic), libva-drm1:amd64 (1.6.1-1, automatic), libnl-route-3-200:amd64 (3.2.26-1, automatic), libhx509-5-heimdal:amd64 (1.6~rc2+dfsg-10, automatic), libkio5:amd64 (4.14.10-3, automatic), libxml2-utils:amd64 (2.9.2+zdfsg1-4, automatic), kate-data:amd64 (4.14.3-2, automatic), libfreerdp-utils1.1:amd64 (1.1.0~git20140921.1.440916e+dfsg1-5, automatic), libudisks2-0:amd64 (2.1.6-2, automatic), libvncclient1:amd64 (0.9.10+dfsg-3, automatic), libplasma3:amd64 (4.14.10-3, automatic), libwinpr-file0.1:amd64 (1.1.0~git20140921.1.440916e+dfsg1-5, automatic), libsmbclient:amd64 (4.1.17+dfsg-4, automatic), libqt4-declarative:amd64 (4.8.7+dfsg-3, automatic), libwinpr-crypto0.1:amd64 (1.1.0~git20140921.1.440916e+dfsg1-5, automatic)
```
that is EVERYTHING this one program installed. It even installed VLC. Which is a great app, but why why why... Anyways yet again back on point I know there's a way I could turn this list into a format I could paste after apt-get purge however I can't find out how. Any suggestions? Basically looks like I need a program I can tell to replace everything between ":amd64" and "), " with a simple " ".

---

### Post by Bucky Ball on 2015-09-29
k3b is a Kubuntu app and any app you install starting with 'K' generally is. All of them will drag in a HEAP of stuff, so avoid.

To kill, uninstall k3b then open a terminal and:

```
sudo apt-get autoremove
```

That should do it.

Isn't Brasero the default burner in Ubuntu? That works fine. If you are looking to make a CD, it shouldn't matter about he burner, so I'm just wondering what the issue was with Brasero. You just drag the files and drop them in then burn the CD. It doesn't care what filetype they are. Most don't.

A lightweight burner, similar to Brasero in look, is xfburn, the default in Xubuntu. No, it won't drag in eight million dependencies. :)

---

### Post by herculeesjr on 2015-09-29
> **Bucky Ball said:**
> k3b is a Kubuntu app and any app you install starting with 'K' generally is. All of them will drag in a HEAP of stuff, so avoid.

To kill, uninstall k3b then open a terminal and:

```
sudo apt-get autoremove
```

That should do it.

Isn't Brasero the default burner in Ubuntu? That works fine. If you are looking to make a CD, it shouldn't matter about he burner, so I'm just wondering what the issue was with Brasero. You just drag the files and drop them in then burn the CD. It doesn't care what filetype they are. Most don't.

A lightweight burner, similar to Brasero in look, is xfburn, the default in Xubuntu. No, it won't drag in eight million dependencies. :)

apt-get autoremove as usual (for me at least) failed to remove even ten of the packages, trying to run it again tells me there's nothing to remove. Also would have helped if I had marked this as Xubuntu, xfburn is the default and refuses to burn flac files despite having the packages it says it needs installed.

---

### Post by Habitual on 2015-09-29
[http://pastie.org/private/0mxyjgz4b1btqgvvefg61a](http://pastie.org/private/0mxyjgz4b1btqgvvefg61a)

Reference: [http://stackoverflow.com/questions/15639080/sed-or-regex-how-to-remove-everything-between-round-brackets](http://stackoverflow.com/questions/15639080/sed-or-regex-how-to-remove-everything-between-round-brackets)

To be honest, this scares the hell out of me, so I accept Zero Responsibility for what you do with your cleaned up list.
I'd be less scared if you had proven backups. ;)

---

### Post by Bucky Ball on 2015-09-29
> **Habitual said:**
> [http://pastie.org/private/0mxyjgz4b1btqgvvefg61a](http://pastie.org/private/0mxyjgz4b1btqgvvefg61a)

Reference: [http://stackoverflow.com/questions/15639080/sed-or-regex-how-to-remove-everything-between-round-brackets](http://stackoverflow.com/questions/15639080/sed-or-regex-how-to-remove-everything-between-round-brackets)

To be honest, this scares the hell out of me, so I accept Zero Responsibility for what you do with your cleaned up list.
I'd be less scared if you had proven backups. ;)

I wouldn't go there. You may well remove some shared dependencies, not positive, but there's some there without 'k', so I wouldn't risk it personally.

> **herculeesjr said:**
> apt-get autoremove as usual (for me at least) failed to remove even ten of the packages ...

Did it give an error message? Please describe specifically. You did this after uninstalling k3b?

```
sudo apt-get remove --purge k3b
```

What do you get? Copy and paste the terminal output between code tags, please (see last link in my signature).

If it works the way you're expecting, go to your /home folder, hit control+h to show hidden files, and delete /.k3b if it is there.

---

### Post by herculeesjr on 2015-09-29
> **Habitual said:**
> [http://pastie.org/private/0mxyjgz4b1btqgvvefg61a](http://pastie.org/private/0mxyjgz4b1btqgvvefg61a)

Reference: [http://stackoverflow.com/questions/15639080/sed-or-regex-how-to-remove-everything-between-round-brackets](http://stackoverflow.com/questions/15639080/sed-or-regex-how-to-remove-everything-between-round-brackets)

To be honest, this scares the hell out of me, so I accept Zero Responsibility for what you do with your cleaned up list.
I'd be less scared if you had proven backups. ;)

That did the trick. \\:D/ All uninstalled and no obvious issues. I'm running a pretty minimal system in the first place, and I verified that the list I posted was a list of apps that were installed at the same time I installed k3b not a full dependencies list. So between that and the fact I break something almost every week and have to reinstall, I'm not worried. Everything important is in the near-impossible-to-access-with-Linux Google Drive.

---

### Post by herculeesjr on 2015-09-29
> **Bucky Ball said:**
> I wouldn't go there. You may well remove some shared dependencies, not positive, but there's some there without 'k', so I wouldn't risk it personally.



Did it give an error message? Please describe specifically. You did this after uninstalling k3b?

```
sudo apt-get remove --purge k3b
```

What do you get? Copy and paste the terminal output between code tags, please (see last link in my signature).

If it works the way you're expecting, go to your /home folder, hit control+h to show hidden files, and delete /.k3b if it is there.

Yes I used apt-get purge k3b and then apt-get autoremove which only removed ```
cdparanoia, cdrdao, genisoimage, wodim, libmagic1, libflac++6v5, libk3b6, libao-common, libao4, libkcddb4, libkcompactdisc4, libmusicbrainz5cc2v5, libneon27-gnutls
```. The rest of that long list remained installed. For me apt-get autoremove is as much of a lie as Windows saying my software was successfully uninstalled. However I'm sure someone with a deeper knowledge of it's inner working will be able to give a good reason why it acts like this.

---

### Post by Habitual on 2015-09-29
Glad it worked out.

---

### Post by SeijiSensei on 2015-09-29
> **Bucky Ball said:**
> k3b is a Kubuntu app and any app you install starting with 'K' generally is. All of them will drag in a HEAP of stuff, so avoid.
Unless you're like me and prefer KDE.

---

