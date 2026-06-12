---
title: "-lbam resolution ?"
date: 2013-01-14
forum: General Help
---

### Post by naragam on 2013-01-14
Hi all,

Looks like -lbam resolution requires the BAM library... Does anybody know how to get the required bam lib for ubuntu 12.05 LTS?

TiA, Nash

---

### Post by steeldriver on 2013-01-14
You might want to install and familiarize yourself with the apt-file tool for answering questions like this

```
$ apt-file search -x 'libbam\..*'
libbam-dev: /usr/lib/libbam.a

```Also apt-cache

```
$ apt-cache show libbam-dev
Package: libbam-dev
Priority: optional
Section: universe/libdevel
Installed-Size: 426
Maintainer: Ubuntu Developers <ubuntu-devel-discuss@lists.ubuntu.com>
Original-Maintainer: Debian Med Packaging Team <debian-med-packaging@lists.alioth.debian.org>
Architecture: i386
Source: samtools
Version: 0.1.18-1ubuntu2
Pre-Depends: dpkg (>= 1.15.6)
Filename: pool/universe/s/samtools/libbam-dev_0.1.18-1ubuntu2_i386.deb
Size: 126446
MD5sum: f909c7aff795cdb6245206be91542104
SHA1: cd5de1ff3df7501af11cdb64d404f1451152919f
SHA256: 4060e7e6c8d4463f9ff8172708a00c223076903783ab8317eb98b74f4578f2ce
Description-en: manipulates nucleotide sequence alignments in BAM or SAM format
 The BAM library provides I/O and various operations on manipulating nucleotide
 sequence alignments in the BAM (Binary Alignment/Mapping) or SAM (Sequence
 Alignment/Map) format. It now supports importing from or exporting to SAM,
 sorting, merging, generating pileup, and quickly retrieval of reads overlapped
 with a specified region.
Homepage: http://samtools.sourceforge.net
Description-md5: 4c789ab81592f6eceeecf3e861006b9f
Bugs: https://bugs.launchpad.net/ubuntu/+filebug
Origin: Ubuntu
```

Cheers

---

