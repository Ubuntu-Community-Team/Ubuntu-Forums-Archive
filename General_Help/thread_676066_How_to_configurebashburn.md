---
title: "How to configurebashburn?"
date: 2008-01-23
forum: General Help
---

### Post by jseiser on 2008-01-23
This is the output of the configuration,
1) CD Writer
The burner is supposed to be entered as 0,0,0 (For SCSI)
ATAPI:0,0,0 or /dev/hdX (For IDE burners)
(Where hdX is the proper drive, like hdc)
You can also use the device name i.e, yahama, sanyo, etc.
if /etc/default/cdrecord is properly configured.
Auto detect mode: type auto
+----------------+-------------+----------------+
(Possible) SCSI DEVICES:
wodim: No such file or directory.
Cannot open SCSI driver!
For possible targets try 'wodim --devices' or 'wodim -scanbus'.
For possible transport specifiers try 'wodim dev=help'.
For IDE/ATAPI devices configuration, see the file README.ATAPI.setup from
the wodim documentation.

(Possible) IDE DEVICES:
WARNING: the ATA: method is considered deprecated on modern kernels!
Use --devices to display the native names.
wodim: No such file or directory.
Cannot open SCSI driver!
For possible targets try 'wodim --devices' or 'wodim -scanbus'.
For possible transport specifiers try 'wodim dev=help'.
For IDE/ATAPI devices configuration, see the file README.ATAPI.setup from
the wodim documentation.

/dev/cdrom /mnt/cdrom   iso9660   ro,user,noauto,unhide   0      0
/dev/cdrom1 /mnt/cdrom1   iso9660   ro,user,noauto,unhide   0      0
/dev/dvd /mnt/dvd   udf   ro,user,noauto,unhide   0      0
---
2)CD Writer Device File
The path to the cdrom device file is usually something like /dev/cdrom or /dev/dvd

List of possible cdrom drives (According to /etc/fstab):


/dev/cdrom /mnt/cdrom   iso9660   ro,user,noauto,unhide   0      0
/dev/cdrom1 /mnt/cdrom1   iso9660   ro,user,noauto,unhide   0      0
/dev/dvd /mnt/dvd   udf   ro,user,noauto,unhide   0      0
----
3)CD-Reader Mount Point

The mountpoint to your cdrom is usually something like /mnt/cdrom or /mnt/dvd
List of possible cdrom drives (According to /etc/fstab):


/dev/cdrom /mnt/cdrom   iso9660   ro,user,noauto,unhide   0      0
/dev/cdrom1 /mnt/cdrom1   iso9660   ro,user,noauto,unhide   0      0
/dev/dvd /mnt/dvd   udf   ro,user,noauto,unhide   0      0

---
I  am clueless, i normally use k3b, but im trying to avoid the kde libraries.  I tried graveman but when i scan for drives it freezes.
Any help would be awesome.

---

