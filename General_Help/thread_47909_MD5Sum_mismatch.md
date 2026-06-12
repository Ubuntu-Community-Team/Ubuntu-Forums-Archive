---
title: "MD5Sum mismatch"
date: 2005-07-10
forum: General Help
---

### Post by s3verian on 2005-07-10
I ran into a md5 mismatch while trying to get skype running.  It's a newly chrooted i386 install on an AMD64 system.  Any words of sage advice?


#:~/Desktop# skype
skype: error while loading shared libraries: libqt-mt.so.3: cannot open shared object file: No such file or directory
#:~/Desktop# apt-cache search libqt-mt.so.3
libqt3c102-mt - Qt GUI Library (Threaded runtime version), Version 3
#:~/Desktop# apt-get install libqt3c102-mt
Reading package lists... Done
Building dependency tree... Done
You might want to run `apt-get -f install' to correct these:
The following packages have unmet dependencies:
  libqt3c102-mt: Depends: libmng1 (>= 1.0.3-1) but it is not going to be installed
  transcode: Depends: libavcodeccvs (>= 2:20050427-0.0~5.04ubp1) but it is not going to be installed
             Depends: libavifile-0.7c102 (>= 1:0.7.38.20030710-1.2) but it is not going to be installed
             Depends: liblcms1 (>= 1.08-1) but it is not going to be installed
             Depends: libmagick6 but it is not going to be installed
E: Unmet dependencies. Try 'apt-get -f install' with no packages (or specify a solution).
#:~/Desktop# apt-get -f install
Reading package lists... Done
Building dependency tree... Done
Correcting dependencies... Done
The following extra packages will be installed:
  aalib1 libavcodeccvs libavifile-0.7c102 libimlib2 liblcms1 libmagick6 slang1
Suggested packages:
  avifile-player avifile-utils avifile-mad-plugin avifile-mjpeg-plugin avifile-vorbis-plugin avifile-win32-plugin avifile-xvid-plugin avifile-divx-plugin liblcms-utils
The following NEW packages will be installed:
  aalib1 libavcodeccvs libavifile-0.7c102 libimlib2 liblcms1 libmagick6 slang1
0 upgraded, 7 newly installed, 0 to remove and 0 not upgraded.
1 not fully installed or removed.
Need to get 654kB/4726kB of archives.
After unpacking 13.0MB of additional disk space will be used.
Do you want to continue [Y/n]?
WARNING: The following packages cannot be authenticated!
  libavcodeccvs
Install these packages without verification [y/N]? Y
Get:1 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hoary/main libimlib2 1.1.2-2.1 [185kB]
Get:2 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hoary/main slang1 1.4.9dbs-8 [296kB]
Get:3 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hoary/main aalib1 1.4p5-22 [50.0kB]
Get:4 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hoary/main liblcms1 1.13-1 [123kB]
Fetched 654kB in 4s (147kB/s)
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/pool/main/i/imlib2/libimlib2_1.1.2-2.1_i386.deb](http://us.archive.ubuntu.com/ubuntu/pool/main/i/imlib2/libimlib2_1.1.2-2.1_i386.deb)  MD5Sum mismatch
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/pool/main/s/slang/slang1_1.4.9dbs-8_i386.deb](http://us.archive.ubuntu.com/ubuntu/pool/main/s/slang/slang1_1.4.9dbs-8_i386.deb)  MD5Sum mismatch
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/pool/main/a/aalib/aalib1_1.4p5-22_i386.deb](http://us.archive.ubuntu.com/ubuntu/pool/main/a/aalib/aalib1_1.4p5-22_i386.deb)  MD5Sum mismatch
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/pool/main/l/lcms/liblcms1_1.13-1_i386.deb](http://us.archive.ubuntu.com/ubuntu/pool/main/l/lcms/liblcms1_1.13-1_i386.deb)  MD5Sum mismatch
E: Unable to fetch some archives, maybe run apt-get update or try with --fix-missing?

---

### Post by crashtest on 2005-07-10
[QUOTE=s3verian]I ran into a md5 mismatch while trying to get skype running.  It's a newly chrooted i386 install on an AMD64 system.  Any words of sage advice?


#:~/Desktop# skype
skype: error while loading shared libraries: libqt-mt.so.3: cannot open shared object file: No such file or directory
#:~/Desktop# apt-cache search libqt-mt.so.3
libqt3c102-mt - Qt GUI Library (Threaded runtime version), Version 3
#:~/Desktop# apt-get install libqt3c102-mt
Reading package lists... Done
Building dependency tree... Done
You might want to run `apt-get -f install' to correct these:
The following packages have unmet dependencies:
  libqt3c102-mt: Depends: libmng1 (>= 1.0.3-1) but it is not going to be installed
  transcode: Depends: libavcodeccvs (>= 2:20050427-0.0~5.04ubp1) but it is not going to be installed
             Depends: libavifile-0.7c102 (>= 1:0.7.38.20030710-1.2) but it is not going to be installed
             Depends: liblcms1 (>= 1.08-1) but it is not going to be installed
             Depends: libmagick6 but it is not going to be installed
E: Unmet dependencies. Try 'apt-get -f install' with no packages (or specify a solution).
#:~/Desktop# apt-get -f install
Reading package lists... Done
Building dependency tree... Done
Correcting dependencies... Done
The following extra packages will be installed:
  aalib1 libavcodeccvs libavifile-0.7c102 libimlib2 liblcms1 libmagick6 slang1
Suggested packages:
  avifile-player avifile-utils avifile-mad-plugin avifile-mjpeg-plugin avifile-vorbis-plugin avifile-win32-plugin avifile-xvid-plugin avifile-divx-plugin liblcms-utils
The following NEW packages will be installed:
  aalib1 libavcodeccvs libavifile-0.7c102 libimlib2 liblcms1 libmagick6 slang1
0 upgraded, 7 newly installed, 0 to remove and 0 not upgraded.
1 not fully installed or removed.
Need to get 654kB/4726kB of archives.
After unpacking 13.0MB of additional disk space will be used.
Do you want to continue [Y/n]?
WARNING: The following packages cannot be authenticated!
  libavcodeccvs
Install these packages without verification [y/N]? Y
Get:1 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hoary/main libimlib2 1.1.2-2.1 [185kB]
Get:2 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hoary/main slang1 1.4.9dbs-8 [296kB]
Get:3 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hoary/main aalib1 1.4p5-22 [50.0kB]
Get:4 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hoary/main liblcms1 1.13-1 [123kB]
Fetched 654kB in 4s (147kB/s)
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/pool/main/i/imlib2/libimlib2_1.1.2-2.1_i386.deb](http://us.archive.ubuntu.com/ubuntu/pool/main/i/imlib2/libimlib2_1.1.2-2.1_i386.deb)  MD5Sum mismatch
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/pool/main/s/slang/slang1_1.4.9dbs-8_i386.deb](http://us.archive.ubuntu.com/ubuntu/pool/main/s/slang/slang1_1.4.9dbs-8_i386.deb)  MD5Sum mismatch
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/pool/main/a/aalib/aalib1_1.4p5-22_i386.deb](http://us.archive.ubuntu.com/ubuntu/pool/main/a/aalib/aalib1_1.4p5-22_i386.deb)  MD5Sum mismatch
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/pool/main/l/lcms/liblcms1_1.13-1_i386.deb](http://us.archive.ubuntu.com/ubuntu/pool/main/l/lcms/liblcms1_1.13-1_i386.deb)  MD5Sum mismatch
E: Unable to fetch some archives, maybe run apt-get update or try with --fix-missing?[/QUOTE]


Remove 'us' from the lines in sources.list, so they say [http://archive.ubuntu.com](http://archive.ubuntu.com)......  There are a couple of other threads about this issue, and this is the recommended fix.  It worked for me, and many others.  If you need more details, you can search the forums for other threads regarding MD5Sum mismatch.

---

### Post by s3verian on 2005-07-10
Wow that was fast.  I just got up to start brushing my teeth, came back with the toothbrush in my mouth thinking that I might want to edit the title of my post, and the answer was already there!

Thanks for the speedy help!!

---

