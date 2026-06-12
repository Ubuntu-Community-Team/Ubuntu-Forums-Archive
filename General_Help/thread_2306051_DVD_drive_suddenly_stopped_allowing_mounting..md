---
title: "DVD drive suddenly stopped allowing mounting."
date: 2015-12-11
forum: General Help
---

### Post by A Traveller on 2015-12-11
Hi all.

On an Ubuntu 12.04 pc, when inserting a DVD into the drive, Ubuntu asked which program to use to open the DVD and upon selecting VLC and entering the password, the DVD icon appeared in Places, Computer and on the Desktop with the title of the DVD, however, not able to play the DVD at this stage.

After carrying out the steps/commands below, can now play the DVD by launching VLC and opening the DVD from within VLC, however, the DVD icon does not appear in Places, Computer or on the Desktop with the title of the DVD and the command "sudo mount /dev/sr0 /cdrom" gives the error "mount: block device /dev/sr0 is write-protected, mounting read-only".

Added to /etc/apt/sources.list:
deb [http://download.videolan.org/pub/debian/stable/](http://download.videolan.org/pub/debian/stable/) /
deb-src [http://download.videolan.org/pub/debian/stable/](http://download.videolan.org/pub/debian/stable/) /

Commands:
apt-get update
apt-get install libdvdcss2

Can anybody suggest what possibly have the above steps done to stop the DVD from mounting like before and how to get it to do it again?

Thanks.

---

