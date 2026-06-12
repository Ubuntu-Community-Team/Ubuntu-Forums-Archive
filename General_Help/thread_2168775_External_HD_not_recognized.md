---
title: "External HD not recognized"
date: 2013-08-19
forum: General Help
---

### Post by jos4 on 2013-08-19
Hi,

I have a external hard disk which is not recognized in Ubuntu. It works fine in Windows.
Using dmesg I get the following output:

[ 2982.564200] Buffer I/O error on device sdb, logical block 0
[ 2985.573886] sd 7:0:0:0: [sdb] Unhandled sense code
[ 2985.573891] sd 7:0:0:0: [sdb]  Result: hostbyte=invalid driverbyte=DRIVER_SENSE
[ 2985.573895] sd 7:0:0:0: [sdb]  Sense Key : Medium Error [current] 
[ 2985.573901] sd 7:0:0:0: [sdb]  Add. Sense: Unrecovered read error
[ 2985.573906] sd 7:0:0:0: [sdb] CDB: Read(10): 28 00 00 00 00 00 00 00 08 00
[ 2985.573918] end_request: critical target error, dev sdb, sector 0

Does anyone have an idea what can cause this?
Thanks

---

### Post by papibe on 2013-08-19
Hi jos4. Welcome to the forum ):P

What brand is it? Is it WD by any chance?

Is it set up to use encryption or requires a password to access it in Windows?

If so, you may need to log into Windows and disable or uninstall those features.

Regards.

---

### Post by r_avital on 2013-08-19
Not sure I can help, but one thing that should be useful to know, are you connecting it as USB or eSata?

You might also want to try the Hardware forum.

Good luck!

---

