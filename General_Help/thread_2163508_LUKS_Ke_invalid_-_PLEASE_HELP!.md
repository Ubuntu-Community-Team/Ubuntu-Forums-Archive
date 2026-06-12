---
title: "LUKS Ke***** invalid - PLEASE HELP!"
date: 2013-07-18
forum: General Help
---

### Post by YWELLC on 2013-07-18
I recently accessed a LUKS partition on an Ubuntu install from a Windows operating system (on a different disk) using the free on the fly encryption program.  I was able to mount it using my passphrase.  After turning off the computer, I tried to boot into Ubuntu and received a "evms activate is not available message."  I booted into a live CD and tried to mount to the drive.  I received an error message from gParted saying the partition table did not match the signature.  I ran fsck and it "fixed" the problem.

I then tried to boot again, and load Ubuntu.  This time, evms activate message did not show up.  It brought me to passphrase screen and I entered my passphrase.  Then I received "unknown file system or bad password options" message."

I booted again into live CD (GRML) I try to unlock the container with:

cryptsetup luksOpen /dev/sda5

I receive an error message stating that LUKS Ke***** 4, 6, and 7 is invalid.  I ran the command again with the debug option:

Invalid ke***** size 8388608 (offset 1032, stripes 0) in ke***** 4 (beyond data offset 2056) and similar for 6 and 7.

blkid shows "/dev/sdb5 UUID="57ei...." TYPE="crypto-LUKS."

Is there any way for me to open this container now, or is it FUBAR?

I realize this is my fault, and I was actually trying to access the container to backup everything.  I have my whole life on there, school work everything.  Any help you could provide would be greatly appreciated.  I would be willing to shell out the few bitcoins I have to make it worth your while.

Thanks

---

