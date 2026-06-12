---
title: "BOOT Error"
date: 2008-05-01
forum: General Help
---

### Post by moman123 on 2008-05-01
Hi 

i have managed to install Ubuntu v8 + Wubi but as soon as i boot the OS hangs while it loading and scanning the disk at %46 with error :

Device /dev/sdb has a logical sector size of 2048 Not all parts of GNU parted support this at the Moment 
& HGHLY Experimental

Any idea...
Thanks,

---

### Post by ago on 2008-05-01
press esc when you boot after windows and choose verbose mode.

Then when it hangs try to press ctrl+alt+f2 to get to a terminal and run

sudo sh /custom-installation/hooks/failure-command.sh

This will generate logs in c:\ubuntu\installation-logs.zip

Pls post them here.

---

### Post by moman123 on 2008-05-01
after i have enabled the v-mode it worked fine

trying to enable the desktop effects now ...which one do u prefer?

Thanks,

---

