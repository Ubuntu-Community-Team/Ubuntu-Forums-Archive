---
title: "Ubuntu hangs on start up"
date: 2015-01-23
forum: General Help
---

### Post by AuroraDizon on 2015-01-23
I have no idea why or how to fix it.  I tried watching the boot with nomodeset and this is what it looks like: [http://i.imgur.com/c2M6vFI.jpg](http://i.imgur.com/c2M6vFI.jpg)
It doesn't say that there is anything wrong it just stops after the last line and hangs there.  :confused: Any help is much appreciated.

---

### Post by Bucky Ball on 2015-01-23
Is this a fresh install? Has the problem happened after an update? Which release and flavour are you using?

---

### Post by AuroraDizon on 2015-01-24
It is 14.10 not a fresh install it is a desktop version standard probably lts I use for a server.  The minecraft (it has more then just minecraft on it) server was lagging so I asked to ssh into it to reboot.  As normal one of the first things I do is run a sudo apt-get update and apt-get upgrade, but I don't remember there being any updates but it was acting a little strange which happens sometimes.  I actually had to get up to manually turn it on after rebooting it via ssh which was odd.  Thank you for the reply.

I tried to start up an old kernel to see if it would load this one says ... [ 106.051235] sd 4:0:0:0: [sdb] Asking for cache data failed
[ 157.763270] sd 4:0:0:0: [sdb] Assuming drive cache: write through.

Tried memory tests and it keeps shutting down.  Took out each piece of ram still shuts down during mem test. 

Passed hp memory test, but then shut down during hard drive test.

Tried to boot ultimate boot cd.. shut down while it was loading.  Guess something in the hardware is messed up. I got parted magic to run off of not ram settings but then it froze after a few minuets and shut down.  I might be able to access root shell from recovery for a bit, is there any way to ssh to save data?

---

### Post by AuroraDizon on 2015-01-25
Update: started in recovery mode, had to drop to root shell to run fsck manually and it started up.

---

