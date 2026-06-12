---
title: "DVD/DVD Rewriter Problems"
date: 2008-03-07
forum: General Help
---

### Post by deakmann on 2008-03-07
Hi,

I`ve bought a machine pre-installed with Ubuntu 7.1. All is fine except i`m having problems with the optical drives.

The drives seem to get easily confused , I first noticed when trying to get DVD working (now ok with VLC), it seems either using both drives at the same time of switching a disk from one to the other causes major problems.
The system seems to lock up for periods then suddenly I can move the mouse for a shorttime before it locks again , eventually i`m able to use the mouse to shutdown.
I looked at etc/fstab posted below , I thought it was odd that the optical drives are listed as hda and hba , isn`t this usually used for HD`s ?

Anyway, please can someone help with this very annoying problem.

# /etc/fstab: static file system information.
#
# <file system> <mount point> <type> <options> <dump> <pass>
proc /proc proc defaults 0 0
# /dev/sda1
UUID=9ead96b8-fee1-4206-828a-6c532cd605ae / ext3 defaults,errors=remount-ro 0 1
# /dev/sda5
UUID=8f15bcaa-31f8-4c81-adae-6b6a9d1a4222 none swap sw 0 0
/dev/hda /media/cdrom0 udf,iso9660 user,noauto,exec 0 0
/dev/hdb /media/cdrom1 udf,iso9660 user,noauto,exec 0 0

---

