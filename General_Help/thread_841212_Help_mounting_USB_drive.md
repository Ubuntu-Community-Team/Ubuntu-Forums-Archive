---
title: "Help mounting USB drive"
date: 2008-06-26
forum: General Help
---

### Post by piltdown1111 on 2008-06-26
I can't get Hardy to mount a Sony Walkman NWZ-S616F. It is shown in Computer as a USB drive - but won't mount.

dmesg produces:

[ 2399.821771] scsi 11:0:0:0: Direct-Access     SONY     WALKMAN          1.00 PQ: 0 ANSI: 0 CCS
[ 2400.212815] ready
[ 2400.213628] sd 11:0:0:0: [sdc] 1875968 2048-byte hardware sectors (3842 MB)
[ 2400.256569] sd 11:0:0:0: [sdc] Write Protect is off
[ 2400.256572] sd 11:0:0:0: [sdc] Mode Sense: 00 2a 00 00
[ 2400.256574] sd 11:0:0:0: [sdc] Assuming drive cache: write through
[ 2400.259686] sd 11:0:0:0: [sdc] 1875968 2048-byte hardware sectors (3842 MB)
[ 2400.302627] sd 11:0:0:0: [sdc] Write Protect is off
[ 2400.302631] sd 11:0:0:0: [sdc] Mode Sense: 00 2a 00 00
[ 2400.302632] sd 11:0:0:0: [sdc] Assuming drive cache: write through
[ 2400.302637]  sdc: sdc1
[ 2400.303591]  sdc: p1 exceeds device capacity
[ 2400.304184] sd 11:0:0:0: [sdc] Attached SCSI removable disk
[ 2400.304214] sd 11:0:0:0: Attached scsi generic sg3 type 0
[ 2400.342991] attempt to access beyond end of device
[ 2400.342995] sdc: rw=0, want=4294967044, limit=7503872
[ 2400.342997] printk: 11 messages suppressed.
[ 2400.342999] Buffer I/O error on device sdc1, logical block 1073741760
[ 2400.343002] attempt to access beyond end of device
[ 2400.343004] sdc: rw=0, want=4294967048, limit=7503872
[ 2400.343005] Buffer I/O error on device sdc1, logical block 1073741761
[ 2400.343008] attempt to access beyond end of device
[ 2400.343009] sdc: rw=0, want=4294967044, limit=7503872
[ 2400.343011] Buffer I/O error on device sdc1, logical block 1073741760
[ 2400.343013] attempt to access beyond end of device
[ 2400.343014] sdc: rw=0, want=4294967048, limit=7503872
[ 2400.343016] Buffer I/O error on device sdc1, logical block 1073741761
[ 2400.343023] attempt to access beyond end of device
[ 2400.343024] sdc: rw=0, want=4294967276, limit=7503872
[ 2400.343026] Buffer I/O error on device sdc1, logical block 1073741818
[ 2400.343028] attempt to access beyond end of device
[ 2400.343029] sdc: rw=0, want=4294967280, limit=7503872
[ 2400.343031] Buffer I/O error on device sdc1, logical block 1073741819
[ 2400.343033] attempt to access beyond end of device
[ 2400.343034] sdc: rw=0, want=4294967276, limit=7503872
[ 2400.343036] Buffer I/O error on device sdc1, logical block 1073741818
[ 2400.343038] attempt to access beyond end of device
[ 2400.343039] sdc: rw=0, want=4294967280, limit=7503872
[ 2400.343041] Buffer I/O error on device sdc1, logical block 1073741819
[ 2400.343071] attempt to access beyond end of device
[ 2400.343073] sdc: rw=0, want=4294967292, limit=7503872
[ 2400.343075] Buffer I/O error on device sdc1, logical block 1073741822
[ 2400.343077] attempt to access beyond end of device
[ 2400.343079] sdc: rw=0, want=4294967292, limit=7503872
[ 2400.343080] Buffer I/O error on device sdc1, logical block 1073741822
[ 2400.343085] attempt to access beyond end of device
[ 2400.343087] sdc: rw=0, want=4294967292, limit=7503872
[ 2400.343091] attempt to access beyond end of device
[ 2400.343093] sdc: rw=0, want=4294967292, limit=7503872
[ 2400.343097] attempt to access beyond end of device
[ 2400.343098] sdc: rw=0, want=4294967292, limit=7503872
[ 2400.343103] attempt to access beyond end of device
[ 2400.343104] sdc: rw=0, want=4294967292, limit=7503872
[ 2400.343109] attempt to access beyond end of device
[ 2400.343111] sdc: rw=0, want=4294967292, limit=7503872
[ 2400.343116] attempt to access beyond end of device
[ 2400.343118] sdc: rw=0, want=4294967228, limit=7503872
[ 2400.343119] attempt to access beyond end of device
[ 2400.343121] sdc: rw=0, want=4294967232, limit=7503872
[ 2400.343126] attempt to access beyond end of device
[ 2400.343127] sdc: rw=0, want=4294967284, limit=7503872
[ 2400.343129] attempt to access beyond end of device
[ 2400.343130] sdc: rw=0, want=4294967288, limit=7503872
[ 2400.343135] attempt to access beyond end of device
[ 2400.343136] sdc: rw=0, want=4294967292, limit=7503872
[ 2400.343141] attempt to access beyond end of device
[ 2400.343143] sdc: rw=0, want=4294967292, limit=7503872


Any ideas?

Thanks

---

### Post by ibutho on 2008-06-26
The system seems to think that your disk is corrupt because its complaining about I/O errors. Can you mount it sucssfully in Windows or another Linux distro?

---

### Post by piltdown1111 on 2008-06-26
Yes, I can use the player in Windows and other Linux distros, specifically Mandriva and Suse.

---

### Post by lolobu on 2008-07-14
This bug is reported here :
[https://bugs.launchpad.net/ubuntu/+bug/209483]("https://bugs.launchpad.net/ubuntu/+bug/209483")
And Benjamin Delagoutte gave a work around in the thread on the 2008-05-11 which requires recompiling hal

---

