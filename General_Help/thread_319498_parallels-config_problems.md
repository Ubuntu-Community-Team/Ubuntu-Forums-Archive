---
title: "parallels-config problems"
date: 2006-12-15
forum: General Help
---

### Post by robin_0.8.2 on 2006-12-15
hey there, I have quite a problem here.
Took advantage of an offer by parallels and bought the latest parallels version because I would like to  create different virtual machines to test different OS's. Same thing as vmware.

finished installation, you need to run the command 'parallels-config'

Here's what I get and where my problem starts:

[: 141: ==: unexpected operator
     Compiling Parallels Workstation 2.2 drivers...
     Drivers have been compiled successfully.
/usr/bin/parallels-config: 175: pushd: not found
/usr/bin/parallels-config: 186: popd: not found
     Installing drivers...
     Starting drivers...
/usr/lib/parallels/autostart/drivers_start: 19: Syntax error: "(" unexpected
Parallels Workstation drivers were successfully configured
and compiled but cannot be started (insmod command failed).
Run 'dmesg' command for more information.
exit: 3: Illegal number: -1


Anybody can help on this?
Parallels users ran into the same issue?
Non-parallels users but with good linux knowledge any clue on this?

Much appreciation for any help
Cheers
R082

---

### Post by sefs on 2006-12-15
You have been struck low by dash ... lol  ... if you are on edgy.

anyway you have two options to fix this I believe...

option 1
--------------------

/usr/lib/parallels/autostart/drivers_stop
/usr/lib/parallels/autostart/drivers_stat
/usr/lib/parallels/autostart/drivers_start
/usr/lib/parallels/tools/network.sh
/usr/bin/parallels-config

open each of the files above and replace the very first line "#!/bin/sh"  to "#!/bin/bash"

NOTE: this will solve your problem with parallels...but not for instance frostwire.  Have you got that installed and is it working?

option 2
----------------
    rm -f /bin/sh
    ln -s /bin/bash /bin/sh 

NOTE: try option 1 first and see if it works to your liking.

---

### Post by robin_0.8.2 on 2006-12-16
ok perfect  thanx a mill. works ok.
no I dont have frostwire installed.....well good to know though

thanx!

R082

---

### Post by k_traxler on 2007-07-09
That all didn' work out for me, but this from the Parallels Team did:

Hello, Sirs.
Please try to use special builds for the 2.6.20 kernel.
[http://download.parallels.com/stuff/...in-en.i386.rpm](http://download.parallels.com/stuff/...in-en.i386.rpm)
[http://download.parallels.com/stuff/...164-lin-en.deb](http://download.parallels.com/stuff/...164-lin-en.deb)
[http://download.parallels.com/stuff/...164-lin-en.tgz](http://download.parallels.com/stuff/...164-lin-en.tgz)

---

