---
title: "sudo broken"
date: 2014-09-14
forum: General Help
---

### Post by cmcanulty on 2014-09-14
I am getting this error today and can't sudo. All I did was chown of my usb stick that was read only by mistake. I also did the recovery mode root prompt and it says I am in the sudo group

```
sudo: /usr/bin/sudo must be owned by uid 0 and have the setuid bit set
```

Here is the whole output of your suggested commands.

```

-rwxr-xr-x  1 cmcanulty root       14640 Nov 29  2012 prtstat
-rwxr-xr-x  1 cmcanulty root         740 Jul  1 11:35 ps2ascii
-rwxr-xr-x  1 cmcanulty root       33857 Oct  8  2012 ps2eps
-rwxr-xr-x  1 cmcanulty root        2794 Jul  1 11:35 ps2epsi
lrwxrwxrwx  1 cmcanulty root          54 Feb 20  2014 ps2frag -> ../share/texlive/texmf-dist/scripts/texlive/ps2frag.sh
-rwxr-xr-x  1 cmcanulty root         272 Jul  1 11:35 ps2pdf
-rwxr-xr-x  1 cmcanulty root         215 Jul  1 11:35 ps2pdf12
-rwxr-xr-x  1 cmcanulty root         215 Jul  1 11:35 ps2pdf13
-rwxr-xr-x  1 cmcanulty root         215 Jul  1 11:35 ps2pdf14
-rwxr-xr-x  1 cmcanulty root        1097 Jul  1 11:35 ps2pdfwr
-rwxr-xr-x  1 cmcanulty root      132944 Jan 22  2014 ps2pk
-rwxr-xr-x  1 cmcanulty root         647 Jul  1 11:35 ps2ps
-rwxr-xr-x  1 cmcanulty root         669 Jul  1 11:35 ps2ps2
lrwxrwxrwx  1 cmcanulty root           8 Jul  1 11:35 ps2txt -> ps2ascii
-rwxr-xr-x  1 cmcanulty root       53329 Mar 27 14:52 psed
lrwxrwxrwx  1 cmcanulty root           9 May  7 12:42 psfaddtable -> psfxtable
lrwxrwxrwx  1 cmcanulty root           9 May  7 12:42 psfgettable -> psfxtable
lrwxrwxrwx  1 cmcanulty root           9 May  7 12:42 psfstriptable -> psfxtable
-rwxr-xr-x  1 cmcanulty root       18808 Feb 18  2013 psfxtable
-rwxr-xr-x  1 cmcanulty root       10320 Feb  7  2013 psidtopgm
lrwxrwxrwx  1 cmcanulty root          54 Feb 20  2014 pslatex -> ../share/texlive/texmf-dist/scripts/texlive/pslatex.sh
lrwxrwxrwx  1 cmcanulty root          54 Feb 20  2014 pst2pdf -> ../share/texlive/texmf-dist/scripts/pst2pdf/pst2pdf.pl
-rwxr-xr-x  1 cmcanulty root       18704 Feb  7  2013 pstopnm
-rwxr-xr-x  1 cmcanulty root       23280 Nov 29  2012 pstree
lrwxrwxrwx  1 cmcanulty root           6 May  7 12:42 pstree.x11 -> pstree
-rwxr-xr-x  1 cmcanulty root       36607 Mar 27 14:52 pstruct
-rwxr-xr-x  1 cmcanulty root        3524 Mar 27 14:52 ptar
-rwxr-xr-x  1 cmcanulty root        2472 Mar 27 14:52 ptardiff
-rwxr-xr-x  1 cmcanulty root        4239 Mar 27 14:52 ptargrep
-rwxr-xr-x  1 cmcanulty root      360976 Jan 22  2014 ptex
-rwxr-xr-x  1 cmcanulty root       47584 Jan 22  2014 ptftopl
-rwxr-xr-x  1 cmcanulty root       64352 Mar 24 03:35 ptx
-rwxr-xr-x  1 cmcanulty root       88120 Apr  4 06:18 pulseaudio
-rwxr-xr-x  1 cmcanulty root        8115 May 20 13:45 purple-remote
-rwxr-xr-x  1 cmcanulty root         776 May 20 13:45 purple-send
-rwxr-xr-x  1 cmcanulty root         635 May 20 13:45 purple-send-async
-rwxr-xr-x  1 cmcanulty root       12076 May 20 13:45 purple-url-handler
-rwxr-xr-x  1 cmcanulty root       10544 Jan  6  2014 pwdx
-rwxr-xr-x  1 cmcanulty root        9966 Jan 13  2014 pxelinux-options
-rwxr-xr-x  1 cmcanulty root        7269 Mar 23 04:17 py3clean
-rwxr-xr-x  1 cmcanulty root       12120 Mar 23 04:17 py3compile
lrwxrwxrwx  1 cmcanulty root          31 May  7 12:42 py3versions -> ../share/python3/py3versions.py
lrwxrwxrwx  1 cmcanulty root          26 May  7 12:42 pybuild -> ../share/dh-python/pybuild
-rwxr-xr-x  1 cmcanulty root        4123 Dec 21  2013 pyclean
-rwxr-xr-x  1 cmcanulty root       11894 Dec 21  2013 pycompile
lrwxrwxrwx  1 cmcanulty root           8 May  7 12:42 pydoc -> pydoc2.7
-rwxr-xr-x  1 cmcanulty root          79 Mar 22 19:55 pydoc2.7
lrwxrwxrwx  1 cmcanulty root           8 May  7 12:42 pydoc3 -> pydoc3.4
-rwxr-xr-x  1 cmcanulty root          79 Apr 11 10:14 pydoc3.4
lrwxrwxrwx  1 cmcanulty root          12 May  7 12:42 pygettext -> pygettext2.7
-rwxr-xr-x  1 cmcanulty root       22097 Mar 22 19:55 pygettext2.7
lrwxrwxrwx  1 cmcanulty root          12 May  7 12:42 pygettext3 -> pygettext3.4
-rwxr-xr-x  1 cmcanulty root       22368 Apr 11 10:14 pygettext3.4
-rwxr-xr-x  1 cmcanulty root         142 Feb 26  2014 pygmentize
-rwxr-xr-x  1 cmcanulty root         217 Jan  7  2014 pyhtmlizer
-rwxr-xr-x  1 cmcanulty root        2348 Dec  6  2010 pyrenamer
lrwxrwxrwx  1 cmcanulty root           9 May  7 12:42 python -> python2.7
lrwxrwxrwx  1 cmcanulty root           9 May  7 12:42 python2 -> python2.7
-rwxr-xr-x  1 cmcanulty root     3349512 Mar 22 19:57 python2.7
lrwxrwxrwx  1 cmcanulty root           9 May  7 12:42 python3 -> python3.4
-rwxr-xr-x  1 cmcanulty root     4061272 Apr 11 10:15 python3.4
-rwxr-xr-x  1 cmcanulty root     4061272 Apr 11 10:15 python3.4m
lrwxrwxrwx  1 cmcanulty root          10 May  7 12:42 python3m -> python3.4m
lrwxrwxrwx  1 cmcanulty root          58 Feb 20  2014 pythontex -> ../share/texlive/texmf-dist/scripts/pythontex/pythontex.py
-rwxr-xr-x  1 cmcanulty root         306 Feb 20  2014 pythontex3
-rwxr-xr-x  1 cmcanulty root         231 Apr 11 10:14 pyvenv-3.4
lrwxrwxrwx  1 cmcanulty root          29 May  7 12:42 pyversions -> ../share/python/pyversions.py
-rwxr-xr-x  1 cmcanulty root       61184 Aug 19 12:20 qapt-batch
-rwxr-xr-x  1 cmcanulty root      131104 Aug 19 12:20 qaptworker2
lrwxrwxrwx  1 cmcanulty root           9 Feb 19  2014 qcollectiongenerator -> qtchooser
lrwxrwxrwx  1 cmcanulty root           9 Feb 19  2014 qdbus -> qtchooser
lrwxrwxrwx  1 cmcanulty root           9 Feb 19  2014 qdbuscpp2xml -> qtchooser
lrwxrwxrwx  1 cmcanulty root           9 Feb 19  2014 qdbusviewer -> qtchooser
lrwxrwxrwx  1 cmcanulty root           9 Feb 19  2014 qdbusxml2cpp -> qtchooser
lrwxrwxrwx  1 cmcanulty root           9 Feb 19  2014 qdoc -> qtchooser
lrwxrwxrwx  1 cmcanulty root           9 Feb 19  2014 qdoc3 -> qtchooser
lrwxrwxrwx  1 cmcanulty root           9 Feb 19  2014 qglinfo -> qtchooser
lrwxrwxrwx  1 cmcanulty root           9 Feb 19  2014 qhelpconverter -> qtchooser
lrwxrwxrwx  1 cmcanulty root           9 Feb 19  2014 qhelpgenerator -> qtchooser
-rwxr-xr-x  1 cmcanulty root      996520 Jun  4  2013 qjackctl
lrwxrwxrwx  1 cmcanulty root           9 Feb 19  2014 qmake -> qtchooser
lrwxrwxrwx  1 cmcanulty root           9 Feb 19  2014 qml -> qtchooser
lrwxrwxrwx  1 cmcanulty root           9 Feb 19  2014 qml1plugindump -> qtchooser
lrwxrwxrwx  1 cmcanulty root           9 Feb 19  2014 qmlbundle -> qtchooser
lrwxrwxrwx  1 cmcanulty root           9 Feb 19  2014 qmlimportscanner -> qtchooser
lrwxrwxrwx  1 cmcanulty root           9 Feb 19  2014 qmlmin -> qtchooser
lrwxrwxrwx  1 cmcanulty root           9 Feb 19  2014 qmlplugindump -> qtchooser
lrwxrwxrwx  1 cmcanulty root           9 Feb 19  2014 qmlprofiler -> qtchooser
lrwxrwxrwx  1 cmcanulty root           9 Feb 19  2014 qmlscene -> qtchooser
lrwxrwxrwx  1 cmcanulty root           9 Feb 19  2014 qmltestrunner -> qtchooser
lrwxrwxrwx  1 cmcanulty root           9 Feb 19  2014 qmlviewer -> qtchooser
-rwxr-xr-x  1 cmcanulty root       88248 Jan 15  2014 qpdf
-rwxr-xr-x  1 cmcanulty root       18784 Feb 18  2014 qpdldecode
-rwxr-xr-x  1 cmcanulty root       10312 Feb  7  2013 qrttoppm
-rwxr-xr-x  1 cmcanulty root       31328 Feb 19  2014 qtchooser
lrwxrwxrwx  1 cmcanulty root           9 Feb 19  2014 qtconfig -> qtchooser
lrwxrwxrwx  1 cmcanulty root           9 Feb 19  2014 qtpaths -> qtchooser
-rwxr-xr-x  1 cmcanulty root        2453 Jun 20 10:40 quirks-handler
-rwxr-xr-x  1 cmcanulty root          43 May 17 10:56 qvlc
-rwxr-xr-x  1 cmcanulty root        1232 Feb 14  2014 rake1.9.1
-rwxr-xr-x  1 cmcanulty root       60440 Apr 15 15:00 ranlib
-rwxr-xr-x  1 cmcanulty root       10408 Dec 18  2013 rarian-example
-rwxr-xr-x  1 cmcanulty root        1495 Dec 18  2013 rarian-sk-config
-rwxr-xr-x  1 cmcanulty root         564 Dec 18  2013 rarian-sk-extract
-rwxr-xr-x  1 cmcanulty root        6280 Dec 18  2013 rarian-sk-gen-uuid
-rwxr-xr-x  1 cmcanulty root       72440 Dec 18  2013 rarian-sk-get-cl
-rwxr-xr-x  1 cmcanulty root         400 Dec 18  2013 rarian-sk-get-content-list
-rwxr-xr-x  1 cmcanulty root         420 Dec 18  2013 rarian-sk-get-extended-content-list
-rwxr-xr-x  1 cmcanulty root         383 Dec 18  2013 rarian-sk-get-scripts
-rwxr-xr-x  1 cmcanulty root        1172 Dec 18  2013 rarian-sk-install
-rwxr-xr-x  1 cmcanulty root       80664 Dec 18  2013 rarian-sk-migrate
-rwxr-xr-x  1 cmcanulty root       56000 Dec 18  2013 rarian-sk-preinstall
-rwxr-xr-x  1 cmcanulty root         822 Dec 18  2013 rarian-sk-rebuild
-rwxr-xr-x  1 cmcanulty root        9526 Dec 18  2013 rarian-sk-update
-rwxr-xr-x  1 cmcanulty root       10320 Feb  7  2013 rasttopnm
-rwxr-xr-x  1 cmcanulty root       10360 Feb  7  2013 rawtopgm
-rwxr-xr-x  1 cmcanulty root       10312 Feb  7  2013 rawtoppm
lrwxrwxrwx  1 cmcanulty root           9 Feb 19  2014 rcc -> qtchooser
lrwxrwxrwx  1 cmcanulty root          21 May  7 12:42 rcp -> /etc/alternatives/rcp
-rwxr-xr-x  1 cmcanulty root      108400 Apr 10 16:31 rctest
lrwxrwxrwx  1 cmcanulty root           9 Feb 14  2014 rdoc -> rdoc1.9.1
-rwxr-xr-x  1 cmcanulty root         789 Feb 14  2014 rdoc1.9.1
-rwxr-xr-x  1 cmcanulty root      426720 Apr 15 15:00 readelf
-rwxr-xr-x  1 cmcanulty root      188472 Oct  1  2012 readom
-rwxr-xr-x  1 cmcanulty root     1003496 Sep 10 16:02 RealtimeSync
lrwxrwxrwx  1 cmcanulty root           3 Dec 30  2013 rec -> sox
-rwxr-xr-x  1 cmcanulty root       14560 Apr 28 11:43 recode-sr-latin
-rwxr-xr-x  1 cmcanulty root        3436 Nov  4  2013 recountdiff
-rwxr-xr-x  1 cmcanulty root       35520 Nov  4  2013 rediff
-rwxr-xr-x  1 cmcanulty root        1582 Apr  4 19:19 regedit
-rwxr-xr-x  1 cmcanulty root        1582 Apr  4 19:19 regsvr32
-rwxr-xr-x  1 cmcanulty root      305344 Jul 15  2013 remmina
lrwxrwxrwx  1 cmcanulty root          24 May  7 12:42 rename -> /etc/alternatives/rename
-rwxr-xr-x  1 cmcanulty root       10432 Jun  3 16:54 rename.ul
-rwxr-xr-x  1 cmcanulty root       45520 Jan  6  2014 rendercheck
-rwxr-xr-x  1 cmcanulty root       10440 Jun  3 16:54 renice
lrwxrwxrwx  1 cmcanulty root           8 Feb 20  2014 repstopdf -> epstopdf
lrwxrwxrwx  1 cmcanulty root           4 May  7 12:42 reset -> tset
-rwxr-xr-x  1 cmcanulty root       18808 Oct 29  2013 resize
-rwxr-xr-x  1 cmcanulty root       18984 Feb 18  2013 resizecons
-rwxr-xr-x  1 cmcanulty root       31328 Jun  3 16:54 resizepart
-rwxr-xr-x  1 cmcanulty root       10488 Jun  3 16:54 rev
-rwxr-xr-x  1 cmcanulty root       87288 Apr 10 16:31 rfcomm
-rwxr-xr-x  1 cmcanulty root       10304 Feb  7  2013 rgb3toppm
-rwxr-xr-x  1 cmcanulty root          30 Jan 18  2014 rgrep
lrwxrwxrwx  1 cmcanulty root           7 Feb 14  2014 ri -> ri1.9.1
-rwxr-xr-x  1 cmcanulty root         189 Feb 14  2014 ri1.9.1
-rwxr-xr-x  1 cmcanulty root      221384 Apr  8 09:58 ristretto
-rwxr-xr-x  1 cmcanulty root       31264 Feb  7  2013 rletopnm
lrwxrwxrwx  1 cmcanulty root          24 May  7 12:42 rlogin -> /etc/alternatives/rlogin
lrwxrwxrwx  1 cmcanulty root          22 May  7 14:46 rmid -> /etc/alternatives/rmid
lrwxrwxrwx  1 cmcanulty root          29 May  7 14:46 rmiregistry -> /etc/alternatives/rmiregistry
-rwxr-xr-x  1 cmcanulty root    15863224 Oct 22  2013 rosegarden
-rwxr-xr-x  1 cmcanulty root         173 Nov 22  2013 routef
-rwxr-xr-x  1 cmcanulty root        1262 Nov 22  2013 routel
-rwxr-xr-x  1 cmcanulty root      377720 Aug  1 18:37 rpcclient
-rwxr-xr-x  1 cmcanulty root       93104 Aug 28 02:02 rpcgen
lrwxrwxrwx  1 cmcanulty root           7 Feb 20  2014 rpdfcrop -> pdfcrop
-rwxr-xr-x  1 cmcanulty root       26880 Oct  1  2012 rpl8
-rwxr-xr-x  1 cmcanulty root       15144 Oct 21  2013 rpm
-rwxr-xr-x  1 cmcanulty root       10512 Oct 21  2013 rpm2cpio
-rwxr-xr-x  1 cmcanulty root       25080 Oct 21  2013 rpmbuild
-rwxr-xr-x  1 cmcanulty root       11032 Oct 21  2013 rpmdb
-rwxr-xr-x  1 cmcanulty root       15064 Oct 21  2013 rpmgraph
-rwxr-xr-x  1 cmcanulty root       11032 Oct 21  2013 rpmkeys
lrwxrwxrwx  1 cmcanulty root           3 Oct 21  2013 rpmquery -> rpm
-rwxr-xr-x  1 cmcanulty root       15192 Oct 21  2013 rpmsign
-rwxr-xr-x  1 cmcanulty root       11288 Oct 21  2013 rpmspec
lrwxrwxrwx  1 cmcanulty root           3 Oct 21  2013 rpmverify -> rpm
lrwxrwxrwx  1 cmcanulty root          21 May  7 12:42 rsh -> /etc/alternatives/rsh
-rwxr-xr-x  1 cmcanulty root        2610 Jan  6  2014 rstart
-rwxr-xr-x  1 cmcanulty root        1435 Jan  6  2014 rstartd
-rwxr-xr-x  1 cmcanulty root      390704 Apr 17 13:12 rsync
lrwxrwxrwx  1 cmcanulty root           6 May  7 12:42 rtstat -> lnstat
lrwxrwxrwx  1 cmcanulty root           9 Feb 14  2014 ruby -> ruby1.9.1
-rwxr-xr-x  1 cmcanulty root        6304 Feb 14  2014 ruby1.9.1
-rwxr-xr-x  1 cmcanulty root       31424 Mar 24 03:35 runcon
-rwxr-xr-x  1 cmcanulty root       17084 May 13  2013 run-mailcap
-rwxr-xr-x  1 cmcanulty root          57 Dec 15  2013 run-with-aspell
lrwxrwxrwx  1 cmcanulty root          23 May  7 12:42 rview -> /etc/alternatives/rview
-rwxr-xr-x  1 cmcanulty root          42 May 17 10:56 rvlc
-rwxr-xr-x  1 cmcanulty root       53329 Mar 27 14:52 s2p
-rwxr-xr-x  1 cmcanulty root       52904 Aug  1 18:37 samba-regedit
-rwxr-xr-x  1 cmcanulty root        1554 Aug  1 18:37 samba-tool
-rwxr-xr-x  1 cmcanulty root      102280 May  9 19:41 sane-find-scanner
-rwxr-xr-x  1 cmcanulty root       10469 Aug 28  2013 savelog
-rwxr-xr-x  1 cmcanulty root       10464 Feb  7  2013 sbigtopgm
-rwxr-xr-x  1 cmcanulty root       48480 May  9 19:41 scanimage
-rwxr-xr-x  1 cmcanulty root      128968 Apr 16  2013 scolily
-rwxr-xr-x  1 cmcanulty root       87216 Dec 14  2013 scor2prt
-rwxr-xr-x  1 cmcanulty root       67680 May 12 12:04 scp
-rwxr-xr-x  1 cmcanulty root          90 May  5 16:13 scp-dbus-service
-rwxr-xr-x  1 cmcanulty root       10520 Feb 18  2013 screendump
-rwxr-xr-x  1 cmcanulty root    11724864 May 16  2013 scribus
-rwxr-xr-x  1 cmcanulty root       14760 Jun  3 16:54 script
-rwxr-xr-x  1 cmcanulty root       10520 Jun  3 16:54 scriptreplay
lrwxrwxrwx  1 cmcanulty root          16 Dec 18  2013 scrollkeeper-config -> rarian-sk-config
lrwxrwxrwx  1 cmcanulty root          17 Dec 18  2013 scrollkeeper-extract -> rarian-sk-extract
lrwxrwxrwx  1 cmcanulty root          18 Dec 18  2013 scrollkeeper-gen-seriesid -> rarian-sk-gen-uuid
lrwxrwxrwx  1 cmcanulty root          16 Dec 18  2013 scrollkeeper-get-cl -> rarian-sk-get-cl
lrwxrwxrwx  1 cmcanulty root          26 Dec 18  2013 scrollkeeper-get-content-list -> rarian-sk-get-content-list
lrwxrwxrwx  1 cmcanulty root          35 Dec 18  2013 scrollkeeper-get-extended-content-list -> rarian-sk-get-extended-content-list
lrwxrwxrwx  1 cmcanulty root          21 Dec 18  2013 scrollkeeper-get-index-from-docpath -> rarian-sk-get-scripts
lrwxrwxrwx  1 cmcanulty root          21 Dec 18  2013 scrollkeeper-get-toc-from-docpath -> rarian-sk-get-scripts
lrwxrwxrwx  1 cmcanulty root          21 Dec 18  2013 scrollkeeper-get-toc-from-id -> rarian-sk-get-scripts
lrwxrwxrwx  1 cmcanulty root          17 Dec 18  2013 scrollkeeper-install -> rarian-sk-install
lrwxrwxrwx  1 cmcanulty root          20 Dec 18  2013 scrollkeeper-preinstall -> rarian-sk-preinstall
lrwxrwxrwx  1 cmcanulty root          17 Dec 18  2013 scrollkeeper-rebuilddb -> rarian-sk-rebuild
lrwxrwxrwx  1 cmcanulty root          17 Dec 18  2013 scrollkeeper-uninstall -> rarian-sk-install
lrwxrwxrwx  1 cmcanulty root          16 Dec 18  2013 scrollkeeper-update -> rarian-sk-update
-rwxr-xr-x  1 cmcanulty root       47848 Oct 21  2013 sdiff
-rwxr-xr-x  1 cmcanulty root      168792 Apr 10 16:31 sdptool
-rwxr-xr-x  1 cmcanulty root      819904 Jan  8  2014 seahorse
lrwxrwxrwx  1 cmcanulty root          11 May  7 12:42 see -> run-mailcap
-rwxr-xr-x  1 cmcanulty root         474 Jan 14  2014 select-default-iwrap
-rwxr-xr-x  1 cmcanulty root        1215 Jun 17  2013 select-editor
-rwxr-xr-x  1 cmcanulty root        1436 Jun 17  2013 sensible-browser
-rwxr-xr-x  1 cmcanulty root        1109 Jun 17  2013 sensible-editor
-rwxr-xr-x  1 cmcanulty root         288 Jun 17  2013 sensible-pager
-rwxr-xr-x  1 cmcanulty root       23040 Jan 15  2014 sensors
-rwxr-xr-x  1 cmcanulty root       14023 Jan 15  2014 sensors-conf-convert
-rwxr-xr-x  1 cmcanulty root       47744 Mar 24 03:35 seq
lrwxrwxrwx  1 cmcanulty root          28 May  7 14:46 servertool -> /etc/alternatives/servertool
lrwxrwxrwx  1 cmcanulty root          15 May  7 12:42 service -> ../sbin/service
-rwxr-xr-x  1 cmcanulty root        1059 Mar 29 06:16 session-installer
-rwxr-xr-x  1 cmcanulty root       14856 Jan  9  2014 session-migration
-rwxr-xr-x  1 cmcanulty root       14640 Feb 17  2014 sessreg
-rwxr-xr-x  1 cmcanulty root       14536 Jun  3 16:54 setarch
-rwxr-xr-x  1 cmcanulty root       18432 Jun 27  2013 setcifsacl
lrwxrwxrwx  1 cmcanulty root          12 May  7 12:42 setfacl -> /bin/setfacl
-rwxr-xr-x  1 cmcanulty root       15000 Apr  9 11:51 setfattr
-rwxr-xr-x  1 cmcanulty root       10480 Feb 18  2013 setkeycodes
-rwxr-xr-x  1 cmcanulty root       10504 Feb 18  2013 setleds
-rwxr-xr-x  1 cmcanulty root       10464 Feb 18  2013 setlogcons
-rwxr-xr-x  1 cmcanulty root       10552 Feb 18  2013 setmetamode
-rwxr-xr-x  1 cmcanulty root       22952 Mar 24 10:36 setpci
-rwxr-xr-x  1 cmcanulty root        6312 Jun  3 16:54 setsid
-rwxr-xr-x  1 cmcanulty root       26992 Jun  3 16:54 setterm
-rwxr-xr-x  1 cmcanulty root       20592 Jan  6  2014 setxkbmap
-rwxr-xr-x  1 cmcanulty root      121152 May 12 12:04 sftp
lrwxrwxrwx  1 cmcanulty root           6 May  7 12:42 sg -> newgrp
-rwxr-xr-x  1 cmcanulty root       14496 Feb  7  2013 sgitopnm
-rwxr-xr-x  1 cmcanulty root         594 Jan 13  2014 sha1pass
-rwxr-xr-x  1 cmcanulty root       43680 Mar 24 03:35 sha1sum
-rwxr-xr-x  1 cmcanulty root       47784 Mar 24 03:35 sha224sum
-rwxr-xr-x  1 cmcanulty root       47784 Mar 24 03:35 sha256sum
-rwxr-xr-x  1 cmcanulty root       51880 Mar 24 03:35 sha384sum
-rwxr-xr-x  1 cmcanulty root       51880 Mar 24 03:35 sha512sum
-rwxr-xr-x  1 cmcanulty root       99872 Mar 12  2014 shares-admin
-rwxr-xr-x  1 cmcanulty root       23176 Aug  1 18:37 sharesec
-rwxr-xr-x  1 cmcanulty root        8594 Mar 27 14:52 shasum
-rwxr-xr-x  1 cmcanulty root     4228832 Jul 15 10:46 shotwell
-rwxr-xr-x  1 cmcanulty root       18784 Feb 18  2013 showconsolefont
-rwxr-xr-x  1 cmcanulty root       11000 Jan  6  2014 showfont
-rwxr-xr-x  1 cmcanulty root       14624 Feb 18  2013 showkey
-rwxr-xr-x  1 cmcanulty root        6312 Feb 17  2014 showrgb
-rwxr-xr-x  1 cmcanulty root       52016 Mar 24 03:35 shred
-rwxr-xr-x  1 cmcanulty root       47840 Mar 24 03:35 shuf
lrwxrwxrwx  1 cmcanulty root          55 Feb 17  2014 simpdftex -> ../share/texlive/texmf-dist/scripts/simpdftex/simpdftex
-rwxr-xr-x  1 cmcanulty root      345592 May  1 17:21 simple-scan
-rwxr-xr-x  1 cmcanulty root       10336 Feb  7  2013 sirtopnm
-rwxr-xr-x  1 cmcanulty root       27536 Apr 15 15:00 size
-rwxr-xr-x  1 cmcanulty root       23088 Jan  6  2014 skill
-rwxr-xr-x  1 cmcanulty root    35868448 May 22 12:55 skype
-rwxr-xr-x  1 cmcanulty root       18856 Jan  6  2014 slabtop
-rwxr-xr-x  1 cmcanulty root       18712 Feb  7  2013 sldtoppm
lrwxrwxrwx  1 cmcanulty root           3 May 12 12:04 slogin -> ssh
-rwxr-xr-x  1 cmcanulty root       18800 Feb 18  2014 slxdecode
-rwxr-xr-x  1 cmcanulty root       35792 Aug  1 18:37 smbcacls
-rwxr-xr-x  1 cmcanulty root      143416 Aug  1 18:37 smbclient
-rwxr-xr-x  1 cmcanulty root       48416 Aug  1 18:37 smbcontrol
-rwxr-xr-x  1 cmcanulty root       23208 Aug  1 18:37 smbcquotas
-rwxr-xr-x  1 cmcanulty root       23128 Aug  1 18:37 smbget
-rwxr-xr-x  1 cmcanulty root       31456 Aug  1 18:37 smbpasswd
-rwxr-xr-x  1 cmcanulty root       14784 Aug  1 18:37 smbspool
-rwxr-xr-x  1 cmcanulty root       44016 Aug  1 18:37 smbstatus
-rwxr-xr-x  1 cmcanulty root        4896 Jun 13  2013 smbtar
-rwxr-xr-x  1 cmcanulty root       10536 Aug  1 18:37 smbta-util
-rwxr-xr-x  1 cmcanulty root       14768 Aug  1 18:37 smbtree
-rwxr-xr-x  1 cmcanulty root       23032 Jan  6  2014 smproxy
-rwxr-xr-x  1 cmcanulty root       14608 Dec 15  2013 sndfile-cmp
-rwxr-xr-x  1 cmcanulty root       14624 Dec 15  2013 sndfile-concat
-rwxr-xr-x  1 cmcanulty root       18728 Dec 15  2013 sndfile-convert
-rwxr-xr-x  1 cmcanulty root       14664 Dec 15  2013 sndfile-deinterleave
-rwxr-xr-x  1 cmcanulty root       14608 Jan 30  2014 sndfile-generate-chirp
-rwxr-xr-x  1 cmcanulty root       18768 Dec 15  2013 sndfile-info
-rwxr-xr-x  1 cmcanulty root       14640 Dec 15  2013 sndfile-interleave
-rwxr-xr-x  1 cmcanulty root       14720 Jan 30  2014 sndfile-jackplay
-rwxr-xr-x  1 cmcanulty root       18728 Dec 15  2013 sndfile-metadata-get
-rwxr-xr-x  1 cmcanulty root       18752 Dec 15  2013 sndfile-metadata-set
-rwxr-xr-x  1 cmcanulty root       10408 Jan 30  2014 sndfile-mix-to-mono
-rwxr-xr-x  1 cmcanulty root       23088 Dec 15  2013 sndfile-play
-rwxr-xr-x  1 cmcanulty root       23608 Jan 30  2014 sndfile-spectrogram
lrwxrwxrwx  1 cmcanulty root           5 May  7 12:42 snice -> skill
-rwxr-xr-x  1 cmcanulty root       31168 Jan 22  2014 soelim
lrwxrwxrwx  1 cmcanulty root          34 Aug 28 15:06 soffice -> ../lib/libreoffice/program/soffice
lrwxrwxrwx  1 cmcanulty root          40 Apr 18 14:24 software-center -> ../share/software-center/software-center
lrwxrwxrwx  1 cmcanulty root          15 Apr 18 14:24 software-center-gtk3 -> software-center
-rwxr-xr-x  1 cmcanulty root        4259 Apr 30 12:59 software-properties-gtk
-rwxr-xr-x  1 cmcanulty root       44072 Aug  5 01:06 solid-hardware
-rwxr-xr-x  1 cmcanulty root       93912 Oct 14  2013 sopranocmd
-rwxr-xr-x  1 cmcanulty root       27472 Oct 14  2013 sopranod
-rwxr-xr-x  1 cmcanulty root      101760 Mar 24 03:35 sort
-rwxr-xr-x  1 cmcanulty root        4369 Aug 28 01:59 sotruss
-rwxr-xr-x  1 cmcanulty root       64736 Dec 30  2013 sox
lrwxrwxrwx  1 cmcanulty root           3 Dec 30  2013 soxi -> sox
-rwxr-xr-x  1 cmcanulty root       10312 Feb  7  2013 spctoppm
-rwxr-xr-x  1 cmcanulty root       19672 Feb 19  2014 spd-say
-rwxr-xr-x  1 cmcanulty root       27360 Jan 16  2014 speaker-test
-rwxr-xr-x  1 cmcanulty root      130344 Feb 19  2014 speech-dispatcher
-rwxr-xr-x  1 cmcanulty root       18646 Mar 27 14:52 splain
-rwxr-xr-x  1 cmcanulty root       64816 Mar 24 03:35 split
-rwxr-xr-x  1 cmcanulty root        3032 Nov  4  2013 splitdiff
-rwxr-xr-x  1 cmcanulty root       10456 Feb 18  2013 splitfont
-rwxr-xr-x  1 cmcanulty root       23152 Aug 28 02:02 sprof
-rwxr-xr-x  1 cmcanulty root       10288 Feb  7  2013 sputoppm
-rwxr-xr-x  1 cmcanulty root      641664 May 12 12:04 ssh
-rwxr-xr-x  1 cmcanulty root      325728 May 12 12:04 ssh-add
-rwxr-xr-x  1 cmcanulty ssh       284784 May 12 12:04 ssh-agent
-rwxr-xr-x  1 cmcanulty root        1456 May  2 04:35 ssh-argv0
lrwxrwxrwx  1 cmcanulty root          29 May  7 13:23 ssh-askpass -> /etc/alternatives/ssh-askpass
-rwxr-xr-x  1 cmcanulty root        9325 Jun  5  2013 ssh-copy-id
-rwxr-xr-x  1 cmcanulty root        7771 Feb 27  2014 ssh-import-id
-rwxr-xr-x  1 cmcanulty root        2118 Feb 27  2014 ssh-import-id-gh
-rwxr-xr-x  1 cmcanulty root        2509 Feb 27  2014 ssh-import-id-lp
-rwxr-xr-x  1 cmcanulty root      403744 May 12 12:04 ssh-keygen
-rwxr-xr-x  1 cmcanulty root      415960 May 12 12:04 ssh-keyscan
-rwxr-xr-x  1 cmcanulty root          64 Dec  3  2011 sshvnc
-rwxr-xr-x  1 cmcanulty root          63 Dec  3  2011 ssvnc
lrwxrwxrwx  1 cmcanulty root          22 Dec  3  2011 ssvncviewer -> ../lib/ssvnc/vncviewer
-rwxr-xr-x  1 cmcanulty root       10360 Feb  7  2013 st4topgm
-rwxr-xr-x  1 cmcanulty root        1001 Apr  4 06:17 start-pulseaudio-kde
-rwxr-xr-x  1 cmcanulty root        1222 Apr  4 06:17 start-pulseaudio-x11
-rwxr-xr-x  1 cmcanulty root        4834 Jun 17  2012 startx
-rwxr-xr-x  1 cmcanulty root        2968 Mar 21 00:24 startxfce4
-rwxr-xr-x  1 cmcanulty root       72576 Mar 24 03:35 stat
-rwxr-xr-x  1 cmcanulty root       64256 Mar 24 03:35 stdbuf
-rwxr-xr-x  1 cmcanulty root      433152 Mar 13  2014 strace
lrwxrwxrwx  1 cmcanulty root          24 May  7 14:45 stream -> /etc/alternatives/stream
-rwxr-xr-x  1 cmcanulty root        6320 Mar  6  2014 stream.im6
-rwxr-xr-x  1 cmcanulty root       27568 Apr 15 15:00 strings
-rwxr-xr-x  1 cmcanulty root      220128 Apr 15 15:00 strip
lrwxrwxrwx  1 cmcanulty root           8 Nov 14  2013 stunnel -> stunnel3
-rwxr-xr-x  1 cmcanulty root        2785 Nov 14  2013 stunnel3
-rwxr-xr-x  1 cmcanulty root      125968 Nov 14  2013 stunnel4
lrwxrwxrwx  1 cmcanulty root          54 Feb 20  2014 sty2dtx -> ../share/texlive/texmf-dist/scripts/sty2dtx/sty2dtx.pl
-rwxr-xr-x  1 cmcanulty root      155008 Feb 10  2014 sudo
lrwxrwxrwx  1 cmcanulty root           4 May  7 12:42 sudoedit -> sudo
-rwxr-xr-x  1 cmcanulty root       81672 Feb 10  2014 sudoreplay
-rwxr-xr-x  1 cmcanulty root       35496 Mar 24 03:35 sum
-rwxr-xr-x  1 cmcanulty root        3123 Dec  3  2011 su-to-root
-rwxr-xr-x  1 cmcanulty root          46 May 17 10:56 svlc
-rwxr-xr-x  1 cmcanulty root          43 Jan 30  2012 synaptic-pkexec
-rwxr-xr-x  1 cmcanulty root       18240 Apr 10 06:04 synclient
-rwxr-xr-x  1 cmcanulty root       80320 Jan 22  2014 synctex
-rwxr-xr-x  1 cmcanulty root       14704 Apr 10 06:04 syndaemon
-rwxr-xr-x  1 cmcanulty root         130 Jul  6  2012 sysinfo
-rwxr-xr-x  1 cmcanulty root       51256 Jan 13  2014 syslinux
-rwxr-xr-x  1 cmcanulty root        1421 Jan 13  2014 syslinux2ansi
-rwxr-xr-x  1 cmcanulty root     1027320 Sep 14 09:13 systemback
-rwxr-xr-x  1 cmcanulty root       93416 Sep 14 09:13 systemback-cli
-rwxr-xr-x  1 cmcanulty root          95 May  5 16:13 system-config-printer
-rwxr-xr-x  1 cmcanulty root          80 May  5 16:13 system-config-printer-applet
-rwxr-xr-x  1 cmcanulty root       35368 Oct 10  2013 t1ascii
-rwxr-xr-x  1 cmcanulty root       40552 Oct 10  2013 t1asm
-rwxr-xr-x  1 cmcanulty root       35336 Oct 10  2013 t1binary
-rwxr-xr-x  1 cmcanulty root       43552 Oct 10  2013 t1disasm
-rwxr-xr-x  1 cmcanulty root       47784 Oct 10  2013 t1mac
-rwxr-xr-x  1 cmcanulty root       43760 Oct 10  2013 t1unmac
-rwxr-xr-x  1 cmcanulty root       14680 Mar 22 15:05 tabs
-rwxr-xr-x  1 cmcanulty root       31392 Mar 24 03:35 tac
-rwxr-xr-x  1 cmcanulty root       64320 Mar 24 03:35 tail
-rwxr-xr-x  1 cmcanulty root       43472 Jan 22  2014 tangle
-rwxr-xr-x  1 cmcanulty root         237 Jan  7  2014 tap2deb
-rwxr-xr-x  1 cmcanulty root         325 Jan  7  2014 tap2rpm
-rwxr-xr-x  1 cmcanulty root         219 Jan  7  2014 tapconvert
-rwxr-xr-x  1 cmcanulty root       18808 Jun  3 16:54 taskset
-rwxr-xr-x  1 cmcanulty root      109064 Jan 22  2014 tbl
lrwxrwxrwx  1 cmcanulty root           8 May  7 12:42 tclsh -> tclsh8.6
-rwxr-xr-x  1 cmcanulty root        6152 Jan  1  2014 tclsh8.5
-rwxr-xr-x  1 cmcanulty root        6168 Jan  2  2014 tclsh8.6
lrwxrwxrwx  1 cmcanulty root          27 May  7 14:42 tdbbackup -> /etc/alternatives/tdbbackup
-rwxr-xr-x  1 cmcanulty root       10440 Oct 21  2013 tdbbackup.tdbtools
-rwxr-xr-x  1 cmcanulty root       10352 Oct 21  2013 tdbdump
-rwxr-xr-x  1 cmcanulty root       10352 Oct 21  2013 tdbrestore
-rwxr-xr-x  1 cmcanulty root       19168 Oct 21  2013 tdbtool
lrwxrwxrwx  1 cmcanulty root          41 Apr 11 06:28 teamviewer -> /opt/teamviewer9/tv_bin/script/teamviewer
-rwxr-xr-x  1 cmcanulty root     1183992 Jan 22  2014 teckit_compile
-rwxr-xr-x  1 cmcanulty root       31328 Mar 24 03:35 tee
lrwxrwxrwx  1 cmcanulty root          24 May  7 12:42 telnet -> /etc/alternatives/telnet
-rwxr-xr-x  1 cmcanulty root       95424 Oct  2  2012 telnet.netkit
-rwxr-xr-x  1 cmcanulty root       35456 Mar 24 03:35 test
-rwxr-xr-x  1 cmcanulty root       23240 Aug  1 18:37 testparm
lrwxrwxrwx  1 cmcanulty root          11 Feb 14  2014 testrb -> testrb1.9.1
-rwxr-xr-x  1 cmcanulty root         299 Feb 14  2014 testrb1.9.1
-rwxr-xr-x  1 cmcanulty root      315616 Jan 22  2014 tex
lrwxrwxrwx  1 cmcanulty root          56 Feb 17  2014 texconfig -> ../share/texlive/texmf-dist/scripts/texlive/texconfig.sh
lrwxrwxrwx  1 cmcanulty root          63 Feb 17  2014 texconfig-dialog -> ../share/texlive/texmf-dist/scripts/texlive/texconfig-dialog.sh
lrwxrwxrwx  1 cmcanulty root          60 Feb 17  2014 texconfig-sys -> ../share/texlive/texmf-dist/scripts/texlive/texconfig-sys.sh
lrwxrwxrwx  1 cmcanulty root          56 Feb 20  2014 texcount -> ../share/texlive/texmf-dist/scripts/texcount/texcount.pl
lrwxrwxrwx  1 cmcanulty root          52 Feb 20  2014 texdef -> ../share/texlive/texmf-dist/scripts/texdef/texdef.pl
lrwxrwxrwx  1 cmcanulty root          51 Feb 20  2014 texdiff -> ../share/texlive/texmf-dist/scripts/texdiff/texdiff
lrwxrwxrwx  1 cmcanulty root          63 Feb 20  2014 texdirflatten -> ../share/texlive/texmf-dist/scripts/texdirflatten/texdirflatten
lrwxrwxrwx  1 cmcanulty root          53 Feb 17  2014 texdoc -> ../share/texlive/texmf-dist/scripts/texdoc/texdoc.tlu
lrwxrwxrwx  1 cmcanulty root          56 Feb 17  2014 texdoctk -> ../share/texlive/texmf-dist/scripts/texdoctk/texdoctk.pl
lrwxrwxrwx  1 cmcanulty root           8 Jan 22  2014 texhash -> mktexlsr
-rwxr-xr-x  1 cmcanulty root       52399 Dec 11  2013 texi2any
-rwxr-xr-x  1 cmcanulty root       58870 Dec 11  2013 texi2dvi
-rwxr-xr-x  1 cmcanulty root        1302 Dec 11  2013 texi2pdf
-rwxr-xr-x  1 cmcanulty root       19048 Dec 11  2013 texindex
lrwxrwxrwx  1 cmcanulty root          55 Feb 17  2014 texlinks -> ../share/texlive/texmf-dist/scripts/texlive/texlinks.sh
lrwxrwxrwx  1 cmcanulty root          64 Feb 20  2014 texliveonfly -> ../share/texlive/texmf-dist/scripts/texliveonfly/texliveonfly.py
lrwxrwxrwx  1 cmcanulty root          65 Feb 20  2014 texloganalyser -> ../share/texlive/texmf-dist/scripts/texloganalyser/texloganalyser
lrwxrwxrwx  1 cmcanulty root           6 Dec 14  2013 texlua -> luatex
lrwxrwxrwx  1 cmcanulty root           6 Dec 14  2013 texluac -> luatex
-rwxr-xr-x  1 cmcanulty root       35184 Jan 22  2014 tftopl
-rwxr-xr-x  1 cmcanulty root       14440 Feb  7  2013 tgatoppm
-rwxr-xr-x  1 cmcanulty root        2295 Oct 10  2013 tgz
-rwxr-xr-x  1 cmcanulty root       18648 Feb  7  2013 thinkjettopbm
lrwxrwxrwx  1 cmcanulty root          56 Feb 17  2014 thumbpdf -> ../share/texlive/texmf-dist/scripts/thumbpdf/thumbpdf.pl
lrwxrwxrwx  1 cmcanulty root           6 May  7 12:42 Thunar -> thunar
-rwxr-xr-x  1 cmcanulty root      753512 Apr  9 04:35 thunar
-rwxr-xr-x  1 cmcanulty root         333 Apr  9 04:35 thunar-settings
-rwxr-xr-x  1 cmcanulty root       43368 Apr 14 02:22 thunar-volman
-rwxr-xr-x  1 cmcanulty root       38984 Apr 14 02:22 thunar-volman-settings
lrwxrwxrwx  1 cmcanulty root          33 Sep  9 07:51 thunderbird -> ../lib/thunderbird/thunderbird.sh
-rwxr-xr-x  1 cmcanulty root       64288 Mar 22 15:05 tic
-rwxr-xr-x  1 cmcanulty root       14504 Jan 22  2014 tie
-rwxr-xr-x  1 cmcanulty root       18600 Feb  7  2013 tifftopnm
-rwxr-xr-x  1 cmcanulty root        6288 Mar 18 11:08 tightvncconnect
-rwxr-xr-x  1 cmcanulty root       18776 Mar 18 11:08 tightvncpasswd
-rwxr-xr-x  1 cmcanulty root       19655 Mar 18 11:08 tightvncserver
-rwxr-xr-x  1 cmcanulty root       14880 Jun 29  2012 time
-rwxr-xr-x  1 cmcanulty root      119440 Mar 12  2014 time-admin
-rwxr-xr-x  1 cmcanulty root       59480 Sep  2 11:30 timedatectl
-rwxr-xr-x  1 cmcanulty root       52496 Mar 24 03:35 timeout
lrwxrwxrwx  1 cmcanulty root          52 Feb 17  2014 tlmgr -> ../share/texlive/texmf-dist/scripts/texlive/tlmgr.pl
-rwxr-xr-x  1 cmcanulty root       14720 Jan  6  2014 tload
-rwxr-xr-x  1 cmcanulty root        4400 May 30  2013 tl-paper
lrwxrwxrwx  1 cmcanulty root          27 May  7 14:46 tnameserv -> /etc/alternatives/tnameserv
-rwxr-xr-x  1 cmcanulty root      261896 May 12  2013 toc2cddb
-rwxr-xr-x  1 cmcanulty root      261896 May 12  2013 toc2cue
-rwxr-xr-x  1 cmcanulty root       14704 Mar 22 15:05 toe
-rwxr-xr-x  1 cmcanulty root      100776 Jan  6  2014 top
-rwxr-xr-x  1 cmcanulty root       95160 May 22  2012 toshset
lrwxrwxrwx  1 cmcanulty root          10 May  7 12:42 touch -> /bin/touch
-rwxr-xr-x  1 cmcanulty root       12627 Jan 22  2014 tpic2pdftex
-rwxr-xr-x  1 cmcanulty root       14744 Mar 22 15:05 tput
-rwxr-xr-x  1 cmcanulty root       43648 Mar 24 03:35 tr
-rwxr-xr-x  1 cmcanulty root       14680 May  7 17:51 tracepath
-rwxr-xr-x  1 cmcanulty root       14688 May  7 17:51 tracepath6
lrwxrwxrwx  1 cmcanulty root          29 May  7 12:42 traceroute6 -> /etc/alternatives/traceroute6
-rwxr-xr-x  1 cmcanulty root       23104 May  7 17:51 traceroute6.iputils
-rwxr-xr-x  1 cmcanulty root      808680 Jul 11 15:03 transmission-gtk
-rwxr-xr-x  1 cmcanulty root       15736 Jan  6  2014 transset
-rwxr-xr-x  1 cmcanulty root         352 Jan  7  2014 trial
-rwxr-xr-x  1 cmcanulty root      495544 Jan 22  2014 troff
-rwxr-xr-x  1 cmcanulty root       51912 Mar 24 03:35 truncate
-rwxr-xr-x  1 cmcanulty root      159104 Mar 20 13:34 trust
-rwxr-xr-x  1 cmcanulty root       18976 Mar 22 15:05 tset
-rwxr-xr-x  1 cmcanulty root       35424 Mar 24 03:35 tsort
-rwxr-xr-x  1 cmcanulty root          63 Dec  3  2011 tsvnc
-rwxr-xr-x  1 cmcanulty root       33256 Jan 22  2014 ttf2afm
-rwxr-xr-x  1 cmcanulty root       68704 Jan 22  2014 ttf2pk
-rwxr-xr-x  1 cmcanulty root       91576 Jan 22  2014 ttf2tfm
-rwxr-xr-x  1 cmcanulty root      101784 Jan 22  2014 ttfdump
-rwxr-xr-x  1 cmcanulty root       10544 Jun  4 10:04 ttfread
-rwxr-xr-x  1 cmcanulty root       27200 Mar 24 03:35 tty
-rwxr-xr-x  1 cmcanulty root         269 Jan  7  2014 twistd
-rwxr-xr-x  1 cmcanulty root       15021 Dec 11  2013 txixml2texi
lrwxrwxrwx  1 cmcanulty root          70 Feb 20  2014 typeoutfileinfo -> ../share/texlive/texmf-dist/scripts/typeoutfileinfo/typeoutfileinfo.sh
-rwxr-xr-x  1 cmcanulty root       38928 Dec 10  2013 tz_convert
-rwxr-xr-x  1 cmcanulty root       13240 Aug 28 01:58 tzselect
lrwxrwxrwx  1 cmcanulty root          10 Sep  2 16:02 ubuntu-bug -> apport-bug
-rwxr-xr-x  1 cmcanulty root        5278 Jun 20 10:40 ubuntu-drivers
-rwxr-xr-x  1 cmcanulty root        7166 Apr 28 17:02 ubuntu-support-status
-rwxr-xr-x  1 cmcanulty root       38832 Jun 30  2013 ucf
-rwxr-xr-x  1 cmcanulty root       19367 Jun 30  2013 ucfq
-rwxr-xr-x  1 cmcanulty root       10458 Jun 30  2013 ucfr
-rwxr-xr-x  1 cmcanulty root       17776 Jan  6  2014 ucs2any
-rwxr-xr-x  1 cmcanulty root       48368 Mar 10  2014 udisksctl
-rwxr-xr-x  1 cmcanulty root      275264 Feb 19  2014 uget-gtk
lrwxrwxrwx  1 cmcanulty root           9 Feb 19  2014 uic -> qtchooser
lrwxrwxrwx  1 cmcanulty root           9 Feb 19  2014 uic3 -> qtchooser
-rwxr-xr-x  1 cmcanulty root       14584 Jun  4  2013 ul
-rwxr-xr-x  1 cmcanulty root      175640 May  9 19:41 umax_pp
-rwxr-xr-x  1 cmcanulty root       45380 Apr  2 16:52 unattended-upgrade
lrwxrwxrwx  1 cmcanulty root          18 May  7 12:42 unattended-upgrades -> unattended-upgrade
-rwxr-xr-x  1 cmcanulty root      816480 Dec  3  2013 unetbootin
-rwxr-xr-x  1 cmcanulty root       31368 Mar 24 03:35 unexpand
-rwxr-xr-x  1 cmcanulty root         530 Feb 18  2013 unicode_stop
-rwxr-xr-x  1 cmcanulty root       39584 Mar 24 03:35 uniq
-rwxr-xr-x  1 cmcanulty root       10504 Feb  9  2014 unity-scope-loader
-rwxr-xr-x  1 cmcanulty root       27200 Mar 24 03:35 unlink
lrwxrwxrwx  1 cmcanulty root          24 May  7 12:42 unlzma -> /etc/alternatives/unlzma
-rwxr-xr-x  1 cmcanulty root          52 Aug 28 13:33 unopkg
lrwxrwxrwx  1 cmcanulty root          27 May  7 14:46 unpack200 -> /etc/alternatives/unpack200
lrwxrwxrwx  1 cmcanulty root          23 May 23 12:10 unrar -> /etc/alternatives/unrar
-rwxr-xr-x  1 cmcanulty root      262192 Oct 23  2013 unrar-nonfree
-rwxr-xr-x  1 cmcanulty root       10432 Jun  3 16:54 unshare
-rwxr-xr-x  1 cmcanulty root       77976 Oct 21  2013 unsquashfs
-rwxr-xr-x  1 cmcanulty root        5940 Nov  4  2013 unwrapdiff
lrwxrwxrwx  1 cmcanulty root           2 May  7 12:42 unxz -> xz
-rwxr-xr-x  1 cmcanulty root      158392 May 13  2013 unzip
-rwxr-xr-x  1 cmcanulty root       76392 May 13  2013 unzipsfx
-rwxr-xr-x  1 cmcanulty root      111208 Jan 22  2014 upbibtex
-rwxr-xr-x  1 cmcanulty root       43544 Jun  9 13:23 update-alternatives
lrwxrwxrwx  1 cmcanulty root          26 May  7 12:42 updatedb -> /etc/alternatives/updatedb
-rwxr-xr-x  1 cmcanulty root       43776 Jun 20  2013 updatedb.mlocate
-rwxr-xr-x  1 cmcanulty root       19088 Nov  5  2013 update-desktop-database
-rwxr-xr-x  1 cmcanulty root        5602 Mar 27 14:18 update-gconf-defaults
-rwxr-xr-x  1 cmcanulty root        4569 Apr 28 17:02 update-manager
-rwxr-xr-x  1 cmcanulty root      126568 Dec  3  2011 update-menus
-rwxr-xr-x  1 cmcanulty root         672 Apr 11 04:59 update-mime-database
-rwxr-xr-x  1 cmcanulty root       48192 Apr 11 04:59 update-mime-database.real
-rwxr-xr-x  1 cmcanulty root       57704 Apr  9 18:06 update-notifier
-rwxr-xr-x  1 cmcanulty root        6177 Jun  1  2012 update-perl-sax-parsers
lrwxrwxrwx  1 cmcanulty root          53 Feb 17  2014 updmap -> ../share/texlive/texmf-dist/scripts/texlive/updmap.pl
lrwxrwxrwx  1 cmcanulty root          57 Feb 17  2014 updmap-sys -> ../share/texlive/texmf-dist/scripts/texlive/updmap-sys.sh
-rwxr-xr-x  1 cmcanulty root       53768 Jan 22  2014 updvitype
-rwxr-xr-x  1 cmcanulty root       14752 Dec 21  2013 upower
-rwxr-xr-x  1 cmcanulty root       61928 Jan 22  2014 uppltotf
-rwxr-xr-x  1 cmcanulty root      367112 Jan 22  2014 uptex
-rwxr-xr-x  1 cmcanulty root       49608 Jan 22  2014 uptftopl
-rwxr-xr-x  1 cmcanulty root       10512 Jan  6  2014 uptime
-rwxr-xr-x  1 cmcanulty root        4216 Apr  8 17:12 usb-devices
-rwxr-xr-x  1 cmcanulty root       23064 Apr  8 17:12 usbhid-dump
-rwxr-xr-x  1 cmcanulty root        6344 Feb 18  2014 usb_printerid
-rwxr-xr-x  1 cmcanulty root       31360 Mar 24 03:35 users
-rwxr-xr-x  1 cmcanulty root      145632 Mar 12  2014 users-admin
-rwxr-xr-x  1 cmcanulty root          90 Jan 21  2011 user-setup
-rwxr-xr-x  1 cmcanulty root       10432 Jun  3 16:54 uuidgen
lrwxrwxrwx  1 cmcanulty root          16 Nov  5  2013 uvcdynctrl -> uvcdynctrl-0.2.4
-rwxr-xr-x  1 cmcanulty root       36016 Nov  5  2013 uvcdynctrl-0.2.4
-rwxr-xr-x  1 cmcanulty root        3674 Oct 29  2013 uxterm
-rwxr-xr-x  1 cmcanulty root        2496 Oct 10  2013 uz
lrwxrwxrwx  1 cmcanulty root          27 Apr  6 23:42 VBoxBalloonCtrl -> ../share/virtualbox/VBox.sh
lrwxrwxrwx  1 cmcanulty root          27 Apr  6 23:42 vboxballoonctrl -> ../share/virtualbox/VBox.sh
-rwxr-xr-x  1 cmcanulty root      684120 Apr  6 23:42 VBoxClient
lrwxrwxrwx  1 cmcanulty root          27 Apr  6 23:42 VBoxHeadless -> ../share/virtualbox/VBox.sh
lrwxrwxrwx  1 cmcanulty root          27 Apr  6 23:42 vboxheadless -> ../share/virtualbox/VBox.sh
lrwxrwxrwx  1 cmcanulty root          27 Apr  6 23:42 VBoxManage -> ../share/virtualbox/VBox.sh
lrwxrwxrwx  1 cmcanulty root          27 Apr  6 23:42 vboxmanage -> ../share/virtualbox/VBox.sh
lrwxrwxrwx  1 cmcanulty root          27 Apr  6 23:42 VBoxSDL -> ../share/virtualbox/VBox.sh
lrwxrwxrwx  1 cmcanulty root          27 Apr  6 23:42 vboxsdl -> ../share/virtualbox/VBox.sh
lrwxrwxrwx  1 cmcanulty root          27 Apr  6 23:42 vboxwebsrv -> ../share/virtualbox/VBox.sh
-rwxr-xr-x  1 cmcanulty root       10240 Oct 15  2013 verve-focus
-rwxr-xr-x  1 cmcanulty root       51640 Jan 22  2014 vftovp
lrwxrwxrwx  1 cmcanulty root          20 May  7 12:42 vi -> /etc/alternatives/vi
lrwxrwxrwx  1 cmcanulty root          22 May  7 12:42 view -> /etc/alternatives/view
-rwxr-xr-x  1 cmcanulty root       23856 Aug 16  2013 viewres
-rwxr-xr-x  1 cmcanulty root      884360 Jan  2  2014 vim.tiny
-rwxr-xr-x  1 cmcanulty root      266144 Feb 26  2014 vinagre
-rwxr-xr-x  1 cmcanulty root       10528 Nov 18  2013 vino-passwd
-rwxr-xr-x  1 cmcanulty root       31840 Nov 18  2013 vino-preferences
-rwxr-xr-x  1 cmcanulty root      510168 Sep 24  2013 virt_mail
lrwxrwxrwx  1 cmcanulty root          27 Apr  6 23:42 VirtualBox -> ../share/virtualbox/VBox.sh
lrwxrwxrwx  1 cmcanulty root          27 Apr  6 23:42 virtualbox -> ../share/virtualbox/VBox.sh
-rwxr-xr-x  1 cmcanulty root    12103400 Sep 24  2013 virtuoso-t
-rwxr-xr-x  1 cmcanulty root       14728 May 17 10:56 vlc
-rwxr-xr-x  1 cmcanulty root       10560 May 17 10:56 vlc-wrapper
-rwxr-xr-x  1 cmcanulty root       14656 Jan 22  2014 vlna
-rwxr-xr-x  1 cmcanulty root       31120 Jan  6  2014 vmstat
-rwxr-xr-x  1 cmcanulty root       10576 Apr 10 04:56 vmwarectrl
-rwxr-xr-x  1 cmcanulty root      113824 Jan 14  2013 vnc4config
-rwxr-xr-x  1 cmcanulty root       18888 Jan 14  2013 vnc4passwd
-rwxr-xr-x  1 cmcanulty root       19402 Jan 14  2013 vnc4server
lrwxrwxrwx  1 cmcanulty root          27 May 17 08:38 vncconfig -> /etc/alternatives/vncconfig
lrwxrwxrwx  1 cmcanulty root          28 Jun 22 09:31 vncconnect -> /etc/alternatives/vncconnect
lrwxrwxrwx  1 cmcanulty root          27 May 17 08:38 vncpasswd -> /etc/alternatives/vncpasswd
lrwxrwxrwx  1 cmcanulty root          27 May 17 08:38 vncserver -> /etc/alternatives/vncserver
lrwxrwxrwx  1 cmcanulty root          27 Jul 16 21:08 vncviewer -> /etc/alternatives/vncviewer
-rwxr-xr-x  1 cmcanulty root       10240 Feb 25  2014 volname
lrwxrwxrwx  1 cmcanulty root          52 Feb 20  2014 vpl2ovp -> ../share/texlive/texmf-dist/scripts/accfonts/vpl2ovp
lrwxrwxrwx  1 cmcanulty root          52 Feb 20  2014 vpl2vpl -> ../share/texlive/texmf-dist/scripts/accfonts/vpl2vpl
-rwxr-xr-x  1 cmcanulty root       59776 Jan 22  2014 vptovf
-rwxr-xr-x  1 cmcanulty root       18896 Mar 31 17:22 vstp
lrwxrwxrwx  1 cmcanulty root          19 May  7 12:42 w -> /etc/alternatives/w
-rwxr-xr-x  1 cmcanulty tty        19024 Jun  3 16:54 wall
-rwxr-xr-x  1 cmcanulty root       23632 Jan  6  2014 watch
-rwxr-xr-x  1 cmcanulty root       60336 Oct 31  2013 wavpack
-rwxr-xr-x  1 cmcanulty root       53272 Aug  1 18:37 wbinfo
-rwxr-xr-x  1 cmcanulty root       10288 Feb  7  2013 wbmptopbm
-rwxr-xr-x  1 cmcanulty root       39648 Mar 24 03:35 wc
-rwxr-xr-x  1 cmcanulty root       67968 Jan 22  2014 weave
-rwxr-xr-x  1 cmcanulty root         614 Mar 23 05:00 web2disk
-rwxr-xr-x  1 cmcanulty root         286 Jul  1 11:35 wftopfa
-rwxr-xr-x  1 cmcanulty root      407696 Feb  7  2014 wget
-rwxr-xr-x  1 cmcanulty root       48112 Apr 10 06:59 whatis
-rwxr-xr-x  1 cmcanulty root       15128 Jun  3 16:54 whereis
lrwxrwxrwx  1 cmcanulty root          10 May  7 12:42 which -> /bin/which
-rwxr-xr-x  1 cmcanulty root       51968 Mar 24 03:35 who
-rwxr-xr-x  1 cmcanulty root       27200 Mar 24 03:35 whoami
-rwxr-xr-x  1 cmcanulty root       52888 Jun 10 16:28 whoopsie
-rwxr-xr-x  1 cmcanulty root      397808 Apr  4 19:21 widl
-rwxr-xr-x  1 cmcanulty root        9748 Apr  4 19:21 wine
-rwxr-xr-x  1 cmcanulty root     1059064 Apr  4 19:21 wine64
-rwxr-xr-x  1 cmcanulty root     2110248 Apr  4 19:21 wine64-preloader
lrwxrwxrwx  1 cmcanulty root           4 Apr  4 19:19 wine-auto -> wine
-rwxr-xr-x  1 cmcanulty root        1582 Apr  4 19:19 wineboot
-rwxr-xr-x  1 cmcanulty root      113248 Apr  4 19:21 winebuild
-rwxr-xr-x  1 cmcanulty root        1582 Apr  4 19:19 winecfg
-rwxr-xr-x  1 cmcanulty root        1582 Apr  4 19:19 wineconsole
lrwxrwxrwx  1 cmcanulty root           7 Apr  4 19:19 winecpp -> winegcc
-rwxr-xr-x  1 cmcanulty root        1582 Apr  4 19:19 winedbg
-rwxr-xr-x  1 cmcanulty root      158624 Apr  4 19:21 winedump
-rwxr-xr-x  1 cmcanulty root        1582 Apr  4 19:19 winefile
lrwxrwxrwx  1 cmcanulty root           7 Apr  4 19:19 wineg++ -> winegcc
-rwxr-xr-x  1 cmcanulty root       35280 Apr  4 19:21 winegcc
-rwxr-xr-x  1 cmcanulty root       95002 Apr  4 19:19 winemaker
-rwxr-xr-x  1 cmcanulty root        1582 Apr  4 19:19 winemine
-rwxr-xr-x  1 cmcanulty root        1582 Apr  4 19:19 winepath
-rwxr-xr-x  1 cmcanulty root       12860 Apr  4 19:21 wine-preloader
-rwxr-xr-x  1 cmcanulty root      425560 Apr  4 19:21 wineserver
-rwxr-xr-x  1 cmcanulty root      640757 Mar  3  2014 winetricks
-rwxr-xr-x  1 cmcanulty root       18656 Feb  7  2013 winicontoppm
lrwxrwxrwx  1 cmcanulty root           7 May  7 12:42 wish -> wish8.6
-rwxr-xr-x  1 cmcanulty root        6192 Mar 12  2014 wish8.6
-rwxr-xr-x  1 cmcanulty root       59944 Apr  4 19:21 wmc
-rwxr-xr-x  1 cmcanulty root      397848 Oct  1  2012 wodim
-rwxr-xr-x  1 cmcanulty root       10376 Dec 15  2013 word-list-compress
-rwxr-xr-x  1 cmcanulty root      133504 Jan 22  2014 wovp2ovf
-rwxr-xr-x  1 cmcanulty root       48024 Mar  5  2014 wpa_passphrase
-rwxr-xr-x  1 cmcanulty root       18872 Jan  6  2014 w.procps
-rwxr-xr-x  1 cmcanulty root      221808 Apr  4 19:21 wrc
-rwxr-xr-x  1 cmcanulty root       43896 Feb 18  2014 wrestool
lrwxrwxrwx  1 cmcanulty root          23 May  7 12:42 write -> /etc/alternatives/write
-rwxr-xr-x  1 cmcanulty root       31864 Oct 31  2013 wvgain
-rwxr-xr-x  1 cmcanulty root       43816 Oct 31  2013 wvunpack
-rwxr-xr-x  1 cmcanulty root      361984 Jan  4  2014 wxcas
-rwxr-xr-x  1 cmcanulty root       10192 Jan 29  2014 X
-rwxr-xr-x  1 cmcanulty root      372744 Jan 14  2013 x0vnc4server
lrwxrwxrwx  1 cmcanulty root          29 May 17 08:38 x0vncserver -> /etc/alternatives/x0vncserver
lrwxrwxrwx  1 cmcanulty root           1 May  7 12:42 X11 -> .
-rwxr-xr-x  1 cmcanulty root      138104 Jan  6  2014 x11perf
-rwxr-xr-x  1 cmcanulty root        2807 Jan  6  2014 x11perfcomp
-rwxr-xr-x  1 cmcanulty root     1608536 May 26  2013 x11vnc
lrwxrwxrwx  1 cmcanulty root           7 Jun  3 16:54 x86_64 -> setarch
lrwxrwxrwx  1 cmcanulty root           9 May  7 12:42 x86_64-linux-gnu-addr2line -> addr2line
lrwxrwxrwx  1 cmcanulty root           2 May  7 12:42 x86_64-linux-gnu-ar -> ar
lrwxrwxrwx  1 cmcanulty root           2 May  7 12:42 x86_64-linux-gnu-as -> as
lrwxrwxrwx  1 cmcanulty root           7 May  7 12:42 x86_64-linux-gnu-c++filt -> c++filt
lrwxrwxrwx  1 cmcanulty root           7 May  7 12:42 x86_64-linux-gnu-cpp -> cpp-4.8
lrwxrwxrwx  1 cmcanulty root           7 May  7 12:42 x86_64-linux-gnu-cpp-4.8 -> cpp-4.8
lrwxrwxrwx  1 cmcanulty root           3 May  7 12:42 x86_64-linux-gnu-dwp -> dwp
lrwxrwxrwx  1 cmcanulty root           7 May  7 12:42 x86_64-linux-gnu-elfedit -> elfedit
lrwxrwxrwx  1 cmcanulty root           7 Apr  7 18:50 x86_64-linux-gnu-g++ -> g++-4.8
lrwxrwxrwx  1 cmcanulty root           7 Apr  5 07:05 x86_64-linux-gnu-g++-4.8 -> g++-4.8
lrwxrwxrwx  1 cmcanulty root           7 May  7 12:42 x86_64-linux-gnu-gcc -> gcc-4.8
lrwxrwxrwx  1 cmcanulty root           7 May  7 12:42 x86_64-linux-gnu-gcc-4.8 -> gcc-4.8
lrwxrwxrwx  1 cmcanulty root          10 May  7 12:42 x86_64-linux-gnu-gcc-ar -> gcc-ar-4.8
lrwxrwxrwx  1 cmcanulty root          10 May  7 12:42 x86_64-linux-gnu-gcc-ar-4.8 -> gcc-ar-4.8
lrwxrwxrwx  1 cmcanulty root          10 May  7 12:42 x86_64-linux-gnu-gcc-nm -> gcc-nm-4.8
lrwxrwxrwx  1 cmcanulty root          10 May  7 12:42 x86_64-linux-gnu-gcc-nm-4.8 -> gcc-nm-4.8
lrwxrwxrwx  1 cmcanulty root          14 May  7 12:42 x86_64-linux-gnu-gcc-ranlib -> gcc-ranlib-4.8
lrwxrwxrwx  1 cmcanulty root          14 May  7 12:42 x86_64-linux-gnu-gcc-ranlib-4.8 -> gcc-ranlib-4.8
lrwxrwxrwx  1 cmcanulty root           8 May  7 12:42 x86_64-linux-gnu-gcov -> gcov-4.8
lrwxrwxrwx  1 cmcanulty root           8 May  7 12:42 x86_64-linux-gnu-gcov-4.8 -> gcov-4.8
lrwxrwxrwx  1 cmcanulty root           5 May  7 12:42 x86_64-linux-gnu-gprof -> gprof
lrwxrwxrwx  1 cmcanulty root           2 May  7 12:42 x86_64-linux-gnu-ld -> ld
lrwxrwxrwx  1 cmcanulty root           6 May  7 12:42 x86_64-linux-gnu-ld.bfd -> ld.bfd
lrwxrwxrwx  1 cmcanulty root           7 May  7 12:42 x86_64-linux-gnu-ld.gold -> ld.gold
lrwxrwxrwx  1 cmcanulty root           2 May  7 12:42 x86_64-linux-gnu-nm -> nm
lrwxrwxrwx  1 cmcanulty root           7 May  7 12:42 x86_64-linux-gnu-objcopy -> objcopy
lrwxrwxrwx  1 cmcanulty root           7 May  7 12:42 x86_64-linux-gnu-objdump -> objdump
lrwxrwxrwx  1 cmcanulty root           6 May  7 12:42 x86_64-linux-gnu-ranlib -> ranlib
lrwxrwxrwx  1 cmcanulty root           7 May  7 12:42 x86_64-linux-gnu-readelf -> readelf
lrwxrwxrwx  1 cmcanulty root           4 May  7 12:42 x86_64-linux-gnu-size -> size
lrwxrwxrwx  1 cmcanulty root           7 May  7 12:42 x86_64-linux-gnu-strings -> strings
lrwxrwxrwx  1 cmcanulty root           5 May  7 12:42 x86_64-linux-gnu-strip -> strip
-rwxr-xr-x  1 cmcanulty root       43624 Jan  6  2014 xargs
-rwxr-xr-x  1 cmcanulty root       40304 Dec  3  2012 xauth
-rwxr-xr-x  1 cmcanulty root       17296 Jan  6  2014 xbiff
-rwxr-xr-x  1 cmcanulty root       10336 Feb  7  2013 xbmtopbm
-rwxr-xr-x  1 cmcanulty root      101792 Mar 31 17:22 xbrlapi
-rwxr-xr-x  1 cmcanulty root       32848 Jan  6  2014 xcalc
-rwxr-xr-x  1 cmcanulty root      663648 Dec 26  2013 xchat
-rwxr-xr-x  1 cmcanulty root       17120 Jan  6  2014 xclipboard
-rwxr-xr-x  1 cmcanulty root       43312 Jan  6  2014 xclock
-rwxr-xr-x  1 cmcanulty root       31728 Feb 17  2014 xcmsdb
-rwxr-xr-x  1 cmcanulty root       16512 Jan  6  2014 xconsole
-rwxr-xr-x  1 cmcanulty root       12648 Jan  6  2014 xcursorgen
-rwxr-xr-x  1 cmcanulty root       11408 Jan  6  2014 xcutsel
-rwxr-xr-x  1 cmcanulty root       15559 Jul 18 05:49 xdg-desktop-icon
-rwxr-xr-x  1 cmcanulty root       38175 Jul 18 05:49 xdg-desktop-menu
-rwxr-xr-x  1 cmcanulty root       21469 Jul 18 05:49 xdg-email
-rwxr-xr-x  1 cmcanulty root       24667 Jul 18 05:49 xdg-icon-resource
-rwxr-xr-x  1 cmcanulty root       34208 Jul 18 05:49 xdg-mime
-rwxr-xr-x  1 cmcanulty root       13794 Jul 18 05:49 xdg-open
-rwxr-xr-x  1 cmcanulty root       25432 Jul 18 05:49 xdg-screensaver
-rwxr-xr-x  1 cmcanulty root       25565 Jul 18 05:49 xdg-settings
-rwxr-xr-x  1 cmcanulty root         234 Apr 11 04:43 xdg-user-dir
-rwxr-xr-x  1 cmcanulty root       19200 Jul  3  2013 xdg-user-dirs-gtk-update
-rwxr-xr-x  1 cmcanulty root       18864 Apr 11 04:43 xdg-user-dirs-update
-rwxr-xr-x  1 cmcanulty root       88368 Jan  6  2014 xditview
-rwxr-xr-x  1 cmcanulty root       32208 Aug 16  2013 xdpyinfo
-rwxr-xr-x  1 cmcanulty root       10376 Aug 16  2013 xdriinfo
-rwxr-xr-x  1 cmcanulty root        3031 Jan 22  2014 xdvi
lrwxrwxrwx  1 cmcanulty root          26 Jun 24 08:01 xdvi.bin -> /etc/alternatives/xdvi.bin
-rwxr-xr-x  1 cmcanulty root      631000 Jan 22  2014 xdvipdfmx
-rwxr-xr-x  1 cmcanulty root      623632 Jan 22  2014 xdvi-xaw
-rwxr-xr-x  1 cmcanulty root      621544 Jan  6  2014 xedit
-rwxr-xr-x  1 cmcanulty root      665736 Jan 22  2014 xetex
-rwxr-xr-x  1 cmcanulty root       27304 Aug 16  2013 xev
-rwxr-xr-x  1 cmcanulty root       20944 Jan  6  2014 xeyes
-rwxr-xr-x  1 cmcanulty root      248840 Mar 12  2014 xfburn
-rwxr-xr-x  1 cmcanulty root      133496 Mar 24 08:43 xfce4-about
-rwxr-xr-x  1 cmcanulty root       47264 Mar 31 07:24 xfce4-accessibility-settings
-rwxr-xr-x  1 cmcanulty root       60416 Mar 31 07:24 xfce4-appearance-settings
-rwxr-xr-x  1 cmcanulty root      125496 May 24  2013 xfce4-appfinder
-rwxr-xr-x  1 cmcanulty root       59448 Feb 20  2014 xfce4-clipman
-rwxr-xr-x  1 cmcanulty root       79928 Feb 20  2014 xfce4-clipman-settings
-rwxr-xr-x  1 cmcanulty root      113160 May 24  2013 xfce4-dict
-rwxr-xr-x  1 cmcanulty root       92440 Mar 31 07:24 xfce4-display-settings
-rwxr-xr-x  1 cmcanulty root       92320 Mar 31 07:24 xfce4-keyboard-settings
-rwxr-xr-x  1 cmcanulty root       51312 Mar 31 07:24 xfce4-mime-settings
-rwxr-xr-x  1 cmcanulty root       84248 Mar 31 07:24 xfce4-mouse-settings
-rwxr-xr-x  1 cmcanulty root      116808 Oct 15  2013 xfce4-notes
-rwxr-xr-x  1 cmcanulty root       22528 Oct 15  2013 xfce4-notes-settings
-rwxr-xr-x  1 cmcanulty root       34816 May 24  2013 xfce4-notifyd-config
-rwxr-xr-x  1 cmcanulty root      297632 Feb 20  2014 xfce4-panel
-rwxr-xr-x  1 cmcanulty root        1568 Feb 20  2014 xfce4-popup-applicationsmenu
-rwxr-xr-x  1 cmcanulty root       10240 Feb 20  2014 xfce4-popup-clipman
-rwxr-xr-x  1 cmcanulty root        1496 Feb 20  2014 xfce4-popup-directorymenu
-rwxr-xr-x  1 cmcanulty root       10240 Oct 15  2013 xfce4-popup-notes
-rwxr-xr-x  1 cmcanulty root        1539 Mar 13  2014 xfce4-popup-places
-rwxr-xr-x  1 cmcanulty root        1540 Mar 19 04:59 xfce4-popup-whiskermenu
-rwxr-xr-x  1 cmcanulty root        1493 Feb 20  2014 xfce4-popup-windowmenu
-rwxr-xr-x  1 cmcanulty root       34888 Jun 17 21:51 xfce4-power-information
-rwxr-xr-x  1 cmcanulty root      149608 Jun 17 21:51 xfce4-power-manager
-rwxr-xr-x  1 cmcanulty root      100440 Jun 17 21:51 xfce4-power-manager-settings
-rwxr-xr-x  1 cmcanulty root       96800 Mar 22 13:07 xfce4-screenshooter
-rwxr-xr-x  1 cmcanulty root       22528 May 26  2013 xfce4-sensors
-rwxr-xr-x  1 cmcanulty root      182504 Mar 21 00:24 xfce4-session
-rwxr-xr-x  1 cmcanulty root       10640 Mar 21 00:24 xfce4-session-logout
-rwxr-xr-x  1 cmcanulty root      104680 Mar 21 00:24 xfce4-session-settings
-rwxr-xr-x  1 cmcanulty root       71920 Mar 31 07:24 xfce4-settings-editor
-rwxr-xr-x  1 cmcanulty root       51360 Mar 31 07:24 xfce4-settings-manager
-rwxr-xr-x  1 cmcanulty root      108776 Jan 10  2014 xfce4-taskmanager
-rwxr-xr-x  1 cmcanulty root      186720 Jan 11  2014 xfce4-terminal
-rwxr-xr-x  1 cmcanulty root        1124 Jan 11  2014 xfce4-terminal.wrapper
-rwxr-xr-x  1 cmcanulty root       26784 Mar 14  2013 xfce4-volumed
-rwxr-xr-x  1 cmcanulty root       27312 Dec 23  2013 xfconf-query
-rwxr-xr-x  1 cmcanulty root       28936 Aug 16  2013 xfd
-rwxr-xr-x  1 cmcanulty root      346216 Apr  9 04:38 xfdesktop
-rwxr-xr-x  1 cmcanulty root      137768 Apr  9 04:38 xfdesktop-settings
-rwxr-xr-x  1 cmcanulty root        1931 Mar 24 08:33 xfhelp4
-rwxr-xr-x  1 cmcanulty root        1560 Mar 21 00:24 xflock4
-rwxr-xr-x  1 cmcanulty root       37184 Aug 16  2013 xfontsel
-rwxr-xr-x  1 cmcanulty root      610312 Oct 29  2013 xfreerdp
lrwxrwxrwx  1 cmcanulty root          15 May  7 12:42 xfrun4 -> xfce4-appfinder
-rwxr-xr-x  1 cmcanulty root      100632 Mar 31 07:24 xfsettingsd
-rwxr-xr-x  1 cmcanulty root        6936 Jan  6  2014 xfsinfo
-rwxr-xr-x  1 cmcanulty root      354344 Apr  9 06:46 xfwm4
-rwxr-xr-x  1 cmcanulty root      100584 Apr  9 06:46 xfwm4-settings
-rwxr-xr-x  1 cmcanulty root       63720 Apr  9 06:46 xfwm4-tweaks-settings
-rwxr-xr-x  1 cmcanulty root      133280 Apr  9 06:46 xfwm4-workspace-settings
-rwxr-xr-x  1 cmcanulty root       10432 Feb 17  2014 xgamma
-rwxr-xr-x  1 cmcanulty root       61192 Jan  6  2014 xgc
-rwxr-xr-x  1 cmcanulty root      263304 Apr 28 11:43 xgettext
-rwxr-xr-x  1 cmcanulty root       14728 Feb 17  2014 xhost
-rwxr-xr-x  1 cmcanulty root       14496 Feb  7  2013 ximtoppm
-rwxr-xr-x  1 cmcanulty root       18912 Jun 17  2012 xinit
-rwxr-xr-x  1 cmcanulty root       48544 Jan 21  2014 xinput
-rwxr-xr-x  1 cmcanulty root        9944 Jan  6  2014 xkbbell
-rwxr-xr-x  1 cmcanulty root      201784 Jan  6  2014 xkbcomp
-rwxr-xr-x  1 cmcanulty root       31704 Jan  6  2014 xkbevd
-rwxr-xr-x  1 cmcanulty root       97912 Jan  6  2014 xkbprint
-rwxr-xr-x  1 cmcanulty root       17792 Jan  6  2014 xkbvleds
-rwxr-xr-x  1 cmcanulty root       16096 Jan  6  2014 xkbwatch
-rwxr-xr-x  1 cmcanulty root       14659 Feb 17  2014 xkeystone
-rwxr-xr-x  1 cmcanulty root       14640 Aug 16  2013 xkill
-rwxr-xr-x  1 cmcanulty root       16016 Jan  6  2014 xload
-rwxr-xr-x  1 cmcanulty root       16880 Jan  6  2014 xlogo
-rwxr-xr-x  1 cmcanulty root       10472 Aug 16  2013 xlsatoms
-rwxr-xr-x  1 cmcanulty root       14648 Aug 16  2013 xlsclients
-rwxr-xr-x  1 cmcanulty root       18784 Aug 16  2013 xlsfonts
-rwxr-xr-x  1 cmcanulty root       38320 Jan  6  2014 xmag
-rwxr-xr-x  1 cmcanulty root       58192 Jan  6  2014 xman
-rwxr-xr-x  1 cmcanulty root       19744 Aug 16  2013 xmessage
-rwxr-xr-x  1 cmcanulty root       18432 Jun 13 09:04 xmlcatalog
-rwxr-xr-x  1 cmcanulty root       64336 Jun 13 09:04 xmllint
lrwxrwxrwx  1 cmcanulty root           9 Feb 19  2014 xmlpatterns -> qtchooser
lrwxrwxrwx  1 cmcanulty root           9 Feb 19  2014 xmlpatternsvalidator -> qtchooser
-rwxr-xr-x  1 cmcanulty root       31552 Feb 17  2014 xmodmap
-rwxr-xr-x  1 cmcanulty root       11184 Jan  6  2014 xmore
-rwxr-xr-x  1 cmcanulty root     2331776 Jul 29 20:23 Xorg
-rwxr-xr-x  1 cmcanulty root       14648 Feb  7  2013 xpmtoppm
-rwxr-xr-x  1 cmcanulty root       37808 Aug 16  2013 xprop
-rwxr-xr-x  1 cmcanulty root       14688 Feb 18  2014 xqxdecode
-rwxr-xr-x  1 cmcanulty root       56024 Feb 17  2014 xrandr
-rwxr-xr-x  1 cmcanulty root       27208 Feb 17  2014 xrdb
-rwxr-xr-x  1 cmcanulty root        6320 Oct 29  2012 xrdp-dis
-rwxr-xr-x  1 cmcanulty root       10440 Oct 29  2012 xrdp-genkeymap
-rwxr-xr-x  1 cmcanulty root       11368 Oct 29  2012 xrdp-keygen
-rwxr-xr-x  1 cmcanulty root       10544 Oct 29  2012 xrdp-sesadmin
-rwxr-xr-x  1 cmcanulty root       14728 Oct 29  2012 xrdp-sesrun
-rwxr-xr-x  1 cmcanulty root       10440 Feb 17  2014 xrefresh
lrwxrwxrwx  1 cmcanulty root          35 May  7 12:42 x-session-manager -> /etc/alternatives/x-session-manager
-rwxr-xr-x  1 cmcanulty root       31336 Feb 17  2014 xset
-rwxr-xr-x  1 cmcanulty root       10424 Feb 17  2014 xsetmode
-rwxr-xr-x  1 cmcanulty root       10432 Feb 17  2014 xsetpointer
-rwxr-xr-x  1 cmcanulty root       18792 Feb 17  2014 xsetroot
-rwxr-xr-x  1 cmcanulty root       44248 Feb  5  2014 xsetwacom
-rwxr-xr-x  1 cmcanulty root       85664 Jan  6  2014 xsm
-rwxr-xr-x  1 cmcanulty root       15152 Feb 17  2014 xstdcmap
-rwxr-xr-x  1 cmcanulty root        4556 Mar 27 14:52 xsubpp
-rwxr-xr-x  1 cmcanulty root      511064 Oct 29  2013 xterm
lrwxrwxrwx  1 cmcanulty root          37 May  7 12:42 x-terminal-emulator -> /etc/alternatives/x-terminal-emulator
-rwxr-xr-x  1 cmcanulty root     1617264 Mar 18 11:08 Xtightvnc
-rwxr-xr-x  1 cmcanulty root      104608 Mar 18 11:08 xtightvncviewer
-rwxr-xr-x  1 cmcanulty root       32704 Feb 17  2014 xvidtune
-rwxr-xr-x  1 cmcanulty root       14576 Aug 16  2013 xvinfo
-rwxr-xr-x  1 cmcanulty root       10328 Feb  7  2013 xvminitoppm
lrwxrwxrwx  1 cmcanulty root          22 May 17 08:38 Xvnc -> /etc/alternatives/Xvnc
-rwxr-xr-x  1 cmcanulty root     4844064 Jan 14  2013 Xvnc4
-rwxr-xr-x  1 cmcanulty root      377392 Jan 14  2013 xvnc4viewer
lrwxrwxrwx  1 cmcanulty root          28 Jul 16 21:08 xvncviewer -> /etc/alternatives/xvncviewer
-rwxr-xr-x  1 cmcanulty root       25888 Jan  6  2014 xwd
-rwxr-xr-x  1 cmcanulty root       18600 Feb  7  2013 xwdtopnm
lrwxrwxrwx  1 cmcanulty root          34 May  7 12:42 x-window-manager -> /etc/alternatives/x-window-manager
-rwxr-xr-x  1 cmcanulty root       39616 Aug 16  2013 xwininfo
-rwxr-xr-x  1 cmcanulty root       23464 Jan  6  2014 xwud
lrwxrwxrwx  1 cmcanulty root          31 May  7 12:42 x-www-browser -> /etc/alternatives/x-www-browser
-rwxr-xr-x  1 cmcanulty root       14736 Jan  2  2014 xxd
-rwxr-xr-x  1 cmcanulty root       68648 Feb 12  2014 xz
lrwxrwxrwx  1 cmcanulty root           2 May  7 12:42 xzcat -> xz
lrwxrwxrwx  1 cmcanulty root           6 May  7 12:42 xzcmp -> xzdiff
-rwxr-xr-x  1 cmcanulty root        5518 Feb 12  2014 xzdiff
lrwxrwxrwx  1 cmcanulty root           6 May  7 12:42 xzegrep -> xzgrep
lrwxrwxrwx  1 cmcanulty root           6 May  7 12:42 xzfgrep -> xzgrep
-rwxr-xr-x  1 cmcanulty root        5421 Feb 12  2014 xzgrep
-rwxr-xr-x  1 cmcanulty root        1825 Feb 12  2014 xzless
-rwxr-xr-x  1 cmcanulty root        2168 Feb 12  2014 xzmore
-rwxr-xr-x  1 cmcanulty root       10312 Feb  7  2013 ybmtopbm
-rwxr-xr-x  1 cmcanulty root       52984 Mar 10  2014 yelp
-rwxr-xr-x  1 cmcanulty root       27200 Mar 24 03:35 yes
-rwxr-xr-x  1 cmcanulty root       10336 Feb  7  2013 yuvsplittoppm
-rwxr-xr-x  1 cmcanulty root       10336 Feb  7  2013 yuvtoppm
-rwxr-xr-x  1 cmcanulty root       14648 Aug 28 02:02 zdump
-rwxr-xr-x  1 cmcanulty root       10320 Feb  7  2013 zeisstopnm
-rwxr-xr-x  1 cmcanulty root      201736 Jan 15  2014 zeitgeist-daemon
-rwxr-xr-x  1 cmcanulty root      127464 Jan 15  2014 zeitgeist-datahub
-rwxr-xr-x  1 cmcanulty root      100784 Apr  7 05:29 zenity
-rwxr-xr-x  1 cmcanulty root      188296 Oct 21  2013 zip
-rwxr-xr-x  1 cmcanulty root       86096 Oct 21  2013 zipcloak
-rwxr-xr-x  1 cmcanulty root       48078 Mar 27 14:52 zipdetails
-rwxr-xr-x  1 cmcanulty root        2953 May 13  2013 zipgrep
-rwxr-xr-x  1 cmcanulty root      158392 May 13  2013 zipinfo
-rwxr-xr-x  1 cmcanulty root       81704 Oct 21  2013 zipnote
-rwxr-xr-x  1 cmcanulty root       81704 Oct 21  2013 zipsplit
-rwxr-xr-x  1 cmcanulty root       27000 Feb 18  2014 zjsdecode
-rwxr-xr-x  1 cmcanulty root       10336 Jan 15  2014 zlib-flate
-rwxr-xr-x  1 cmcanulty root       47424 Apr 10 06:59 zsoelim
cmcanulty@ubuntu1:~$ ls -la /usr/bin | grep -v "rwxr-xr-x\|^l"
total 308144
cmcanulty@ubuntu1:~$ chmod 4755 /usr/bin/sudo
cmcanulty@ubuntu1:~$ ud
sudo: /usr/bin/sudo must be owned by uid 0 and have the setuid bit set
cmcanulty@ubuntu1:~$ ls -ld /usr /usr/bin
drwxr-xr-x 11 cmcanulty root  4096 May  7 15:12 /usr
drwxr-xr-x  2 cmcanulty root 69632 Sep 14 10:55 /usr/bin
cmcanulty@ubuntu1:~$  ls -l /usr/bin/sudo
-rwsr-xr-x 1 cmcanulty root 155008 Feb 10  2014 /usr/bin/sudo
cmcanulty@ubuntu1:~$ sudo chmod 755 /usr/bin
sudo: /usr/bin/sudo must be owned by uid 0 and have the setuid bit set
cmcanulty@ubuntu1:~$ 
```

thank you I am stuck until this is fixed

---

### Post by cmcanulty on 2014-09-14
I have tried recovery mode with root prompt to fix and no luck. Suddenly I get this error and have lost all root privileges but root prompt says I am a member of sudoers as I should be. 

```
cmcanulty@ubuntu1:~$ ud
sudo: error in /etc/sudo.conf, line 0 while loading plugin `sudoers_policy'
sudo: /usr/lib/sudo/sudoers.so must be owned by uid 0
sudo: fatal error, unable to load plugins
cmcanulty@ubuntu1:~$ 
```

---

### Post by JKyleOKC on 2014-09-14
Check the properties of /usr/lib/sudo/sudoers.so to see who owns it now, and change it back if necessary while booted to a root prompt in recovery mode. The permissions should be -rw-r--r-- so change them also if they differ.

---

### Post by steeldriver on 2014-09-14
***I have moved your other related post into this thread***

---

### Post by JKyleOKC on 2014-09-14
> **cmcanulty said:**
> I am getting this error today and can't sudo. All I did was chown of my usb stick that was read only by mistake. I also did the recovery mode root prompt and it says I am in the sudo group

```
sudo: /usr/bin/sudo must be owned by uid 0 and have the setuid bit set
```

thank you I am stuck until this is fixedYour listing for "sudo" shows > -rwxr-xr-x  1 cmcanulty root      155008 Feb 10  2014 sudoWhere (according to the error message you show) it should be > -rwsr-xr-x  1 root root      155008 Feb 10  2014 sudo

EDIT: My other post does not show the setuid bit being set, but was taken directly from my own working system. I do not know why this discrepancy exists.

It appears that one of the suggested commands made recursive changes to this entire directory, which may break many other utilities besides sudo! You may be able to repair the sudo permissions from recovery mode, however.

In general, recursive ( -R ) changes to any system areas are usually a guarantee of severe system damage requiring a complete reinstall of the system. Don't trust all the suggests you find on the web, even from such usually reliable sites as this one!

---

### Post by Impavidus on 2014-09-15
Everything in your /usr/bin seems owned by you, where everything there (with one or two exceptions) should be owned by root. Everything in your /usr/bin has permissions 755 (with the exception of the symlinks of course), where there should be a few dozen files with the setuid and/or setgid bits set. And as it seems the problem is not isolated to /usr/bin, as /usr also seems affected. It seems that you chmodded and chowned your /usr. The only way to fix is manually repairing all those files, and as we don't know which software you have installed we can't provide you with a complete list of files that have to be fixed. There could be hundreds of them.

The fastest way out is reinstalling.

---

### Post by cmcanulty on 2014-09-15
So can you tell me the command to use  to do that? All I did was try to make my usb stick writable. Thanks

---

### Post by steeldriver on 2014-09-15
Can you scroll back through your command history and see exactly what command you used? it looks like you changed ownership of everything in at least your /usr/bin directory (possibly your whole filesystem)

---

### Post by cmcanulty on 2014-09-15
```
cmcanulty@ubuntu1:~$ history
    1  ud
    2  set uid
    3  ud
    4  mount -o rw,remount /
    5  sudo mount -o rw,remount /
    6  gksudo nautilus
    7  ud
    8  ls -al /etc | grep sudoers
    9  -r--r----- 1 root root 609 2010-05-31 14:53 sudoers
   10  ls -al /etc/sudoers.d
   11  ud
   12  sudo gedit /usr/bin/sudo
   13  ud
   14  history
cmcanulty@ubuntu1:~$
```

---

### Post by cmcanulty on 2014-09-15
I reinstalled. I tried this because I couldn't write to my flash drive. What is wrong with that command? I thought it meant chown of the flash drive (ADATA) recursively.

```
sudo chown -R cmcanulty /media/cmcanulty/ADATA
```

---

