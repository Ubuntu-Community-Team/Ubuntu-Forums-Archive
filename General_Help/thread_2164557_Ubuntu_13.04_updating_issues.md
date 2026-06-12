---
title: "Ubuntu 13.04 updating issues"
date: 2013-07-31
forum: General Help
---

### Post by chambogorden on 2013-07-31
Okay, so after updating two of my laptops(one is a Toshiba Satellite C655 and the other a Dell Inspiron 15) and restarting, when turing on the computer, the 'Dell will only get past the BIOS and claims the boot drive(internal hard drive) is not present, yet it shows up fine in the BIOS settings, as for the Toshiba, it gets to the Ubuntu start up screen and starts to restart from the Ubuntu start up screen and has to be turned off manually, also, I was able to get some errors from the Toshiba:

fsck from util-linux 2.20.1
/dev/sda1 contains a file system with errors, check forced.
/dev/sda1: Error while reading over extent tree in inode 20253: Corrupt extant header

/dev/sda1: UNEXPECTED INCONSISTENCY; RUN fsck MANUALLY
             (i.e., without -a or -p options)
mountall: fsck / [312] terminated with status 4
mountall: Filesystem has errors: /
udevd[446]: '/usr/sbin/alsact1 restore 0' [723] terminated by signal 11 (Segmentation fault)

And this repeats, and as this only happened after the update, I am uncertain of what to do, particularly as the Dell has several GiB of files that I need for college and work. So what should I do? I am unable to update my current laptop for fears the same thing will happen, trying to load the Toshiba with the older system kernal, will update with results. Also, on the Dell it is Kubuntu 13.04 but not on the Toshiba, if it helps.

---

### Post by chambogorden on 2013-07-31
Okay, for trying to load from older kernal build came up with errors as well:

fsck from util-linux 2.20.1
/dev/sda1 contains a file system with errors, check forced.
/dev/sda1: Error while reading over extent tree in inode 20253: Corrupt extant header

/dev/sda1: UNEXPECTED INCONSISTENCY; RUN fsck MANUALLY
             (i.e., without -a or -p options)
mountall: fsck / [313] terminated with status 4
mountall: Filesystem has errors: /
udevd[451]: '/usr/sbin/alsact1 restore 0' [730] terminated by signal 11 (Segmentation fault)


most of it seems to be the same though.

---

