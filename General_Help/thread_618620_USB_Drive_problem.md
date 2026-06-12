---
title: "USB Drive problem"
date: 2007-11-20
forum: General Help
---

### Post by JimmyTheSaint on 2007-11-20
Hi

I am having trouble with a USB drive and before I bin the thing I wanted to make sure!

When I plug it in to my laptop (running Ubuntu 6.10) nothing happens at all. Places -> Computer does show a folder called Generic USB Flash Drive but if I try and mount it it will not work.

The output from /var/logs/messages is as follows:

Nov 20 21:28:44 james-laptop kernel: [17184161.368000]     Additional sense: Cannot read medium - incompatible format
Nov 20 21:28:44 james-laptop kernel: [17184161.368000] end_request: I/O error, dev sda, sector 120
Nov 20 21:28:44 james-laptop kernel: [17184161.384000] sd 3:0:0:0: SCSI error: return code = 0x8000002
Nov 20 21:28:44 james-laptop kernel: [17184161.384000] sda: Current: sense key: Medium Error
Nov 20 21:28:44 james-laptop kernel: [17184161.384000]     Additional sense: Cannot read medium - incompatible format
Nov 20 21:28:44 james-laptop kernel: [17184161.384000] end_request: I/O error, dev sda, sector 64
Nov 20 21:28:44 james-laptop kernel: [17184161.392000] sd 3:0:0:0: SCSI error: return code = 0x8000002
Nov 20 21:28:44 james-laptop kernel: [17184161.392000] sda: Current: sense key: Medium Error
Nov 20 21:28:44 james-laptop kernel: [17184161.392000]     Additional sense: Cannot read medium - incompatible format
Nov 20 21:28:44 james-laptop kernel: [17184161.392000] end_request: I/O error, dev sda, sector 120

The thing is the drive is brand new but I just can't get into the thing to format it or anything. Can anyone give me any help? Thanks

---

### Post by magicfab on 2007-11-20
It seems to be recognized, although with a "format error". Try loading gparted or another partition editor and formatting it to ext3 or else.

---

### Post by JimmyTheSaint on 2007-11-20
I have got GParted but I can't get anywhere with that either!

When I switch to the /dev/sda drive the only option I have is to add a New disklabel but then this fails.

The partition and filesystem show as unallocated for /dev/sda

---

### Post by brownknight on 2008-03-07
Bump!

I am trying out Hardy Heron Alpha 5 now. I have a 2.0 GB USB Drive. It is working fine with Gutsy but when I inserted it in Hardy it gave this error: 

ubuntu@ubuntulinux:~$ dmesg |tail
[ 4400.681303] end_request: I/O error, dev sdb, sector 0
[ 4400.681305] Buffer I/O error on device sdb, logical block 0
[ 4402.991768] sd 6:0:0:0: [sdb] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE,SUGGEST_OK
[ 4402.991773] sd 6:0:0:0: [sdb] Sense Key : Medium Error [current] 
[ 4402.991776] sd 6:0:0:0: [sdb] Add. Sense: Cannot read medium - incompatible format
[ 4402.991781] end_request: I/O error, dev sdb, sector 8
[ 4400.711612] sd 6:0:0:0: [sdb] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE,SUGGEST_OK
[ 4400.711617] sd 6:0:0:0: [sdb] Sense Key : Medium Error [current] 
[ 4400.711620] sd 6:0:0:0: [sdb] Add. Sense: Cannot read medium - incompatible format
[ 4400.711625] end_request: I/O error, dev sdb, sector 0

I noticed that when I mounted the USB in Hardy, it found an autoexec.bat file and Hardy is asking if I wanted to execute this file and of course gave a warning that it is not safe to run this file if I am not sure of it. I answered no - and cancelled the operation. Could this be the problem?

The USB drive icon shows up when I browse the computer but when I click it, it gives a "Unable to Mount Location" error.

---

