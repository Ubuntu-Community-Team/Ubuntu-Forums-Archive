---
title: "Confused! Ubuntu 18.04 sata DVD drives not reading disks"
date: 2020-09-19
forum: General Help
---

### Post by tman69 on 2020-09-19
I am trying to make an ARM machine using tutorials [https://b3n.org/automatic-ripping-machine/](https://b3n.org/automatic-ripping-machine/) or [https://blog.lohannes.com/2018/08/automatic-disk-ripping-machine-full.html](https://blog.lohannes.com/2018/08/automatic-disk-ripping-machine-full.html) yes - these are a bit old. Did a complete fresh install of 18.04. The system has 4 sata DVD drives and when I insert a disk in any drive I get the same errors showing in dmesg regardless if it is a movie disk or the install disk I used to make the system.

From dmesg:

[  109.454413] print_req_error: I/O error, dev sr0, sector 9162240
[  109.490455] sr 1:0:0:0: [sr0] tag#8 FAILED Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[  109.490457] sr 1:0:0:0: [sr0] tag#8 Sense Key : Illegal Request [current]
[  109.490460] sr 1:0:0:0: [sr0] tag#8 Add. Sense: Read of scrambled sector without authentication
[  109.490462] sr 1:0:0:0: [sr0] tag#8 CDB: Read(10) 28 00 00 22 f3 80 00 00 02 00
[  109.490463] print_req_error: I/O error, dev sr0, sector 9162240



Output from lshw -C disk: 

  *-cdrom
       description: DVD-RAM writer
       product: DVD RW AD-7240S
       vendor: Optiarc
       physical id: 0.0.0
       bus info: scsi@1:0.0.0
       logical name: /dev/cdrom
       logical name: /dev/sr0
       version: 1.02
       capabilities: removable audio cd-r cd-rw dvd dvd-r dvd-ram
       configuration: ansiversion=5 status=ready
     *-medium
          physical id: 0
          logical name: /dev/cdrom
  *-cdrom
       description: DVD-RAM writer
       product: DVD RW AD-7240S
       vendor: Optiarc
       physical id: 0.0.0
       bus info: scsi@2:0.0.0
       logical name: /dev/sr1
       version: 1.03
       capabilities: removable audio cd-r cd-rw dvd dvd-r dvd-ram
       configuration: ansiversion=5 status=ready
     *-medium
          physical id: 0
          logical name: /dev/sr1
  *-cdrom
       description: DVD-RAM writer
       product: DVD RW AD-7240S
       vendor: Optiarc
       physical id: 0.0.0
       bus info: scsi@4:0.0.0
       logical name: /dev/dvd
       logical name: /dev/dvdrw
       logical name: /dev/sr2
       version: 1.03
       capabilities: removable audio cd-r cd-rw dvd dvd-r dvd-ram
       configuration: ansiversion=5 status=ready
     *-medium
          physical id: 0
          logical name: /dev/dvd
          capabilities: partitioned partitioned:dos
          configuration: signature=718c7796
  *-cdrom
       description: DVD-RAM writer
       product: DVD RW AD-7240S
       vendor: Optiarc
       physical id: 0.0.0
       bus info: scsi@5:0.0.0
       logical name: /dev/cdrw
       logical name: /dev/sr3
       version: 1.03
       capabilities: removable audio cd-r cd-rw dvd dvd-r dvd-ram
       configuration: ansiversion=5 status=nodisc




These are entries in fstab:

/dev/sr0 /mnt/dev/sr0 udf,iso9660 user,noauto,exec,utf8 0 0
/dev/sr1 /mnt/dev/sr1 udf,iso9660 user,noauto,exec,utf8 0 0
/dev/sr2 /mnt/dev/sr2 udf,iso9660 user,noauto,exec,utf8 0 0
/dev/sr3 /mnt/dev/sr3 udf,iso9660 user,noauto,exec,utf8 0 0



No matter which disk drive I use they all give the same errors. I am intermediate with linux but would be happy to provide any command output if someone is willing to help me out.

Also I do have these installed:



libdvd-pkg/bionic,now 1.4.2-1-1 all [installed]
libdvdcss-dev/now 1.4.2-1~local amd64 [installed,local]
libdvdcss2/now 1.4.2-1~local amd64 [installed,local]



Thanks!

---

