---
title: "Update: cannot load repository info"
date: 2015-02-09
forum: General Help
---

### Post by mringer on 2015-02-09
L-Ub 12.04 (I think). Ran update manager. Initial list was:

Changes for the versions:
Installed version: 5.09-2ubuntu0.5
Available version: 5.09-2ubuntu0.6

Version 5.09-2ubuntu0.6: 

  * SECURITY UPDATE: DoS via insufficient note headers
    - debian/patches/CVE-2014-3710.patch: handle running out of not headers
      in src/readelf.c.
    - CVE-2014-3710
  * SECURITY UPDATE: DoS in ELF parser
    - debian/patches/CVE-2014-8116.patch: limit number of headers and
      capabilities in src/elfclass.h, src/readelf.c.
    - CVE-2014-8116
  * SECURITY UPDATE: DoS via missing recursion limits
    - debian/patches/CVE-2014-8117.patch: lower recursion level and allow
      it to be set from the command line in src/file.{c,h},
      src/file_opts.h, src/funcs.c, src/magic.c, src/magic.h,
      src/softmagic.c, add new option to documentation in
      doc/file.man, doc/libmagic.man.
    - CVE-2014-8117
  * SECURITY UPDATE: DoS via long pascal strings
    - debian/patches/pr398-truncate-pascal-strings.patch: correctly
      calculate size in src/softmagic.c.
    - No CVE number




 Check button produced these errors:

Failed to download repository info:

W:Failed to fetch [http://ppa.launchpad.net/michael-gruz/canon/ubuntu/dists/precise/main/source/Sources](http://ppa.launchpad.net/michael-gruz/canon/ubuntu/dists/precise/main/source/Sources)  404  Not Found
, W:Failed to fetch [http://ppa.launchpad.net/michael-gruz/canon/ubuntu/dists/precise/main/binary-i386/Packages](http://ppa.launchpad.net/michael-gruz/canon/ubuntu/dists/precise/main/binary-i386/Packages)  404  Not Found
, E:Some index files failed to download. They have been ignored, or old ones used instead.



Please any advice? Thank you

---

### Post by plucky on 2015-02-09
Disable the PPA in Software Sources as that PPA doesn't have a repository for Precise [See Here](http://ppa.launchpad.net/michael-gruz/canon/ubuntu/dists/)

Is Lubuntu 12.04 still supported? [See Here](https://help.ubuntu.com/community/Lubuntu/PreviousReleases) Basically No

Good Luck

---

### Post by oldrocker99 on 2015-02-09
Uh, 12.04 of any Ubuntu flavor **should** be supported until 2017.

---

### Post by QIII on 2015-02-09
Lubuntu 12.04 was not an LTS.

---

### Post by mringer on 2015-02-09
Thank you who replied. You have persuaded me that I should upgrade to 14.04. 
My further Qs are off-topic. I will start a new thread on something like
"how to upgrade with Broadcom card"

---

### Post by pdc on 2015-02-10
hi mringer;

if wanting guidance on broadcom, chili555 has a most excellent guide [http://ubuntuforums.org/showthread.php?t=2214110](http://ubuntuforums.org/showthread.php?t=2214110)

---

