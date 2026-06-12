---
title: "Unable to unpack archive"
date: 2015-06-10
forum: General Help
---

### Post by chris137 on 2015-06-10
Hi,
A few days ago my raspberry Pi crashed somehow and the SD card got corrupted.
Luckily I remembered my almost forgotten weekly updates.
Unfortunatly "almost forgotten" means: Remembered there where backups, forgot what they are.
So now I got a few files for the last 4 weeks and don't know what to do with them.
Since the day I wrote the backup-script is a few month back I have absolutely no recollection of that.

The file's mime-type is application/gzip but I can't unpack it with any tool:
```
$ unrar e 2015-06-03

UNRAR 5.00 beta 8 freeware      Copyright (c) 1993-2013 Alexander Roshal

2015-06-03 is not RAR archive
No files to extract

$ unzip 2015-06-03
Archive:  2015-06-03
  End-of-central-directory signature not found.  Either this file is not
  a zipfile, or it constitutes one disk of a multi-part archive.  In the
  latter case the central directory and zipfile comment will be found on
  the last disk(s) of this archive.
unzip:  cannot find zipfile directory in one of 2015-06-03 or
        2015-06-03.zip, and cannot find 2015-06-03.ZIP, period.

$ gunzip --force 2015-06-03
gzip: 2015-06-03: unknown suffix -- ignored
```

Any idea on how to get to know more about the file and how to get the data?
I thought I might have done it using rsync since the backups are stored on my NAS but that wouldn't pack them somehow right?

---

### Post by papibe on 2015-06-10
Hi chris137.

Could you post the output of these commands?
```
file 2015-06-03

gunzip --version

apt-cache policy unzip

unzip -v
```
Regards.

---

### Post by chris137 on 2015-06-10
```
$ file 2015-06-03
2015-06-03: gzip compressed data, from Unix, last modified: Wed Jun  3 03:00:02 2015, max speed

$ gunzip --version
gunzip (gzip) 1.6
Copyright (C) 2007, 2011-2013 Free Software Foundation, Inc.
This is free software.  You may redistribute copies of it under the terms of
the GNU General Public License <http://www.gnu.org/licenses/gpl.html>.
There is NO WARRANTY, to the extent permitted by law.

Written by Paul Eggert.

$ apt-cache policy unzip
unzip:
  Installiert:           6.0-9ubuntu1.3
  Installationskandidat: 6.0-9ubuntu1.3
  Versionstabelle:
 *** 6.0-9ubuntu1.3 0
        500 http://de.archive.ubuntu.com/ubuntu/ trusty-updates/main amd64 Packages
        500 http://security.ubuntu.com/ubuntu/ trusty-security/main amd64 Packages
        100 /var/lib/dpkg/status
     6.0-9ubuntu1 0
        500 http://de.archive.ubuntu.com/ubuntu/ trusty/main amd64 Packages

$ unzip -v
UnZip 6.00 of 20 April 2009, by Debian. Original by Info-ZIP.

Latest sources and executables are at ftp://ftp.info-zip.org/pub/infozip/ ;
see ftp://ftp.info-zip.org/pub/infozip/UnZip.html for other sites.

Compiled with gcc 4.8.2 for Unix (Linux ELF) on Feb 17 2015.

UnZip special compilation options:
        ACORN_FTYPE_NFS
        COPYRIGHT_CLEAN (PKZIP 0.9x unreducing method not supported)
        SET_DIR_ATTRIB
        SYMLINKS (symbolic links supported, if RTL and file system permit)
        TIMESTAMP
        UNIXBACKUP
        USE_EF_UT_TIME
        USE_UNSHRINK (PKZIP/Zip 1.x unshrinking method supported)
        USE_DEFLATE64 (PKZIP 4.x Deflate64(tm) supported)
        UNICODE_SUPPORT [wide-chars, char coding: UTF-8] (handle UTF-8 paths)
        LARGE_FILE_SUPPORT (large files over 2 GiB supported)
        ZIP64_SUPPORT (archives using Zip64 for large files supported)
        USE_BZIP2 (PKZIP 4.6+, using bzip2 lib version 1.0.6, 6-Sept-2010)
        VMS_TEXT_CONV
        WILD_STOP_AT_DIR
        [decryption, version 2.11 of 05 Jan 2007]

UnZip and ZipInfo environment options:
           UNZIP:  [none]
        UNZIPOPT:  [none]
         ZIPINFO:  [none]
      ZIPINFOOPT:  [none]
```
I just got the idea maybe I actually used rsync and then used a command which put its output into one large file.

The whole thing is weird because as I know I would have tested the backup right when I finished the script. - But maybe I didn't.

---

### Post by papibe on 2015-06-10
Thanks, it looks a proper gzip file.

Try renaming the file so that it would have a gz extention:
```
mv -iv 2015-06-03 2015-06-03.gz
```
And then try to unzip it:
```
gunzip 2015-06-03.gz
```
Let us know how that goes.
Regards.

---

### Post by chris137 on 2015-06-11
That worked!
Man, I tried something similar: I renamed it to 2015-06-03.gzip and that did not work.
Now .gz works. I get an image which I was able to dd to my SD card.

Thanks!

---

