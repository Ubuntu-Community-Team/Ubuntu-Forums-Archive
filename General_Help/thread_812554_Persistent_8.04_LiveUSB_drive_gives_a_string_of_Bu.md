---
title: "Persistent 8.04 LiveUSB drive gives a string of Buffer I/O Errors on shutdown"
date: 2008-05-30
forum: General Help
---

### Post by drewster1829 on 2008-05-30
I finally got my Ubuntu 8.04 LiveUSB persistent pen drive (SanDisk Cruzer Micro 4.0GB with U3 removed) to boot from the 2nd partition (the first partition is a 1.5 GB or so blank FAT32, so I can still used it as a normal pen drive on a Windows machine), but when using the persistent feature and changing settings, the OS gives a string of errors: "Buffer I/O error: logical block:" etc

When asking for a shutdown, it will do as the LiveCD and say "Remove any discs from drive and press ENTER:" or something like that.  If you leave the pen drive in and press ENTER, it results in a string of buffer I/O errors (and subsequently randomly corrupted configuration files for the persistent feature).  The errors also occur if removing the drive before hitting enter.

There is nothing in any of the log files (I checked them all) on casper-rw on the USB key indicating these buffer I/O errors (I'm assuming because they occur right before shutdown).  I found other people having problems with buffer I/O errors sometime during the boot process, but not during shutdown.

The random corruption of config files is very annoying(several hidden directories, including /.ICEauthority, which apparently is required for GNOME to start, were unreadable after a recent shutdown).  It really reduces the usefulness of the persistent feature on the drive.  If I get this sorted out (which is what I'm assuming the buffer I/O errors are causing), it will be much more useful for my purposes.  Thanks in advance!

EDIT: Lookie what I found. [https://bugs.launchpad.net/ubuntu/+source/casper/+bug/125702]("https://bugs.launchpad.net/ubuntu/+source/casper/+bug/125702")
Seems to be the bug report for the trouble I'm having.

---

### Post by drewster1829 on 2008-05-30
Alright, the bug report above is the problem I'm having, but the solution is to revert the 3 upstart packages to the Edgy version.  However, Edgy is no longer supported (as of 4-25-08?), so I can't actually get that particular version of upstart anymore.  Is it possible to find an Edgy Eft iso, then burn and/or mount it and use that to get the old upstart packages?

I did reformat the casper-rw partition to ext3 (instead of using ext2, like it says on pendrive linux).  This seems to reduce the filesystem damage caused by not umounting cleanly (fscking it doesn't produce any errors), but it doesn't eliminate the original problem, the buffer I/O errors.

I'm telling ya, my LiveUSB persistent pen drive is 99% there--if I could just eliminate these errors on shutdown, it'll be perfect!

---

