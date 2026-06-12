---
title: "buffer I/O error on device sdb1 phone memory stick"
date: 2007-05-13
forum: General Help
---

### Post by crucial123 on 2007-05-13
celeron based pc
sony ericsson w810

New to ubuntu  (which I am loving)

I have installed multisync plus libmultisync-plugins-all
set up synchronization pairs with Ximan Evolution as first pair
IrMC as second 

plug in phone.....no PHONE or PHONE CARD shows up  (on desktop and in Home Folder)
  (which may be normal)
set phone to file transfer mode and both PHONE or PHONE CARD show up and 
their folders can be navigated, music and photos copied etc.

but now to sync......................

/dev/ttyS0 test locks up the Multisync test applet
/dev/ttys1 returns failed result
/dev/ttyACM0 returns failed result
/dev/ttyACM1 returns failed result

Run dmesg  and things go for a crapper

I have determined, by trial and rebooting that SCSI device sdb is my removable sandisk card in my phone.
    (I have two, the 4gig which shows below and a 1gig, both behave the same way)


[  143.168308] SCSI device sdb: 7999298 512-byte hdwr sectors (4096 MB)
[  143.181302] sdb: Write Protect is off
[  143.181310] sdb: Mode Sense: 00 6a 00 00
[  143.181313] sdb: assuming drive cache: write through
[  143.182069]  sdb: sdb1
[  143.199293]  sdb: p1 exceeds device capacity                                          HERE WE GO!
[  143.203845] sd 1:0:0:0: Attached scsi removable disk sdb
[  143.220929] sd 0:0:0:0: Attached scsi generic sg0 type 0
[  143.221620] sd 1:0:0:0: Attached scsi generic sg1 type 0
[  143.473319] attempt to access beyond end of device
[  143.473331] sdb: rw=0, want=7999300, limit=7999298
[  143.473335] Buffer I/O error on device sdb1, logical block 3999554
[  143.474198] attempt to access beyond end of device
[  143.474209] sdb: rw=0, want=7999302, limit=7999298
[  143.474212] Buffer I/O error on device sdb1, logical block 3999555

If I unmount the PHONE and the PHONE CARD and run dmesg again the I/O error persists

Rebooting clears things up and I get a "normal" dmesg result which ends at line 79.xxxxxx  

Help me please.  Windows crashed and I never want to see it again, but my contact list is on  firefox windows  and on my phone.. I figured it would be easy to just sync my phone to evolution

---

