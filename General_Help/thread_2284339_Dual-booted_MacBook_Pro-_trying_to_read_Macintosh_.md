---
title: "Dual-booted MacBook Pro- trying to read Macintosh HD from Ubuntu"
date: 2015-06-28
forum: General Help
---

### Post by petercworthington on 2015-06-28
Hi, I recently dual booted my MacBook using rEFInd and it all works perfectly except for one thing: attempting to mount the main HFS+ OSX partition while in Ubuntu results in this error:

> Error mounting /dev/sda2 at /media/blah/Macintosh HD: Command-line `mount -t "hfsplus" -o "uhelper=udisks2,nodev,nosuid" "/dev/sda2" "/media/blah/Macintosh HD"' exited with non-zero exit status 32: mount: wrong fs type, bad option, bad superblock on /dev/sda2,       missing codepage or helper program, or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so

I googled the error message but most of the OPs in the threads I found were attempting to read stand-alone drives. Most of the suggestions said that the HFS+ drive was corrupted, but that doesn't make sense because I can still boot into OSX, and verifying the drive while in OSX gave no errors. I also tried installing hfsutils and hfsprogs but this did nothing. I really need to access the data from that partition while in Ubuntu or else dualbooting is pointless for me. I've tried mounting from terminal as well as from the file manager.

(PS: I'm running 14.04 LTS)

---

