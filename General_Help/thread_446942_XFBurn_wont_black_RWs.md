---
title: "XFBurn wont black RWs"
date: 2007-05-17
forum: General Help
---

### Post by Montsegur87 on 2007-05-17
After a quick search in the forums the solution to this porblem was to downgrade to 0.0.3 .

The problem is still there.

This is the log

```
scsidev: '/dev/hda'
devname: '/dev/hda'
scsibus: -2 target: -2 lun: -2
Error trying to open /dev/hda exclusively (Device or resource busy)... retrying in 1 second.
Error trying to open /dev/hda exclusively (Device or resource busy)... retrying in 1 second.
Error trying to open /dev/hda exclusively (Device or resource busy)... retrying in 1 second.
Error trying to open /dev/hda exclusively (Device or resource busy)... retrying in 1 second.
Error trying to open /dev/hda exclusively (Device or resource busy)... giving up.
scsidev: 'ATA:/dev/hda'
TOC Type: 1 = CD-ROM
devname: 'ATA:/dev/hda'
scsibus: -2 target: -2 lun: -2
wodim: No such file or directory. 
Cannot open SCSI driver!
For possible targets try 'wodim --devices' or 'wodim -scanbus'.
For possible transport specifiers try 'wodim dev=help'.
For IDE/ATAPI devices configuration, see the file README.ATAPI.setup from
the wodim documentation.
```

EDIT: I downloaded GnomeBaker and I could black th RW. It seems XFburn is still prety much beta.

---

