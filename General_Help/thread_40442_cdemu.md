---
title: "cdemu"
date: 2005-06-09
forum: General Help
---

### Post by [pl]ice on 2005-06-09
i have installed latest cdemu. 
cdemu -s shows  0:     1   CD_Image_File_CD1.cue
 but when i'm trying to moun it :
:/spare/torrent/pelne/Wesele # mount -t iso9660 /dev/cdemu/0 /a
mount: block device /dev/cdemu/0 is write-protected, mounting read-only
mount: wrong fs type, bad option, bad superblock on /dev/cdemu/0,
       missing codepage or other error
       (could this be the IDE device where you in fact use
       ide-scsi so that sr0 or sda or so is needed?)
       In some cases useful info is found in syslog - try
       dmesg | tail  or so


dmesg:

end_request: I/O error, dev cdemu0, sector 64
isofs_fill_super: bread failed, dev=cdemu0, iso_blknum=16, block=32


that happens to all of my .cue files :(

thanks

---

