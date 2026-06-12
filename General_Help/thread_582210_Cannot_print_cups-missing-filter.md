---
title: "Cannot print: cups-missing-filter"
date: 2007-10-19
forum: General Help
---

### Post by 0x656b694d on 2007-10-19
Hi,

After the upgrade i cannot use my printer. "Printer status" says:
"Printer 'Phaser_3122': 'cups-missing-filter'"

I tried to reinstall printer drivers, nothing help. It worked before.

I will really appreciate any help!

-Mike.

---

### Post by 0x656b694d on 2007-10-20
Okay,

I've found out that some filters were not copied from the driver distro. Copied it manually to /usr/lib/cups/filter/.

But i still cannot print. I get the following error in the CUPS error log:

Unable to open file "/var/spool/cups/d00026-001" - Permission denied

Here is the access attributes of the file:
-rw-r----- 1 root root  /var/spool/cups/d00026-001

How do i setup users and groups (cupsys, lp, lpadmin) to get rid of this error?

Thanks!

---

### Post by ydo on 2008-03-18
I guess the files should have group=lp, thats what they have here..
# chgrp -R lp /var/spool/cups/

also note that cups does not work with libtrash, you need to start cups with it disabled, was a showstopper for me.

---

