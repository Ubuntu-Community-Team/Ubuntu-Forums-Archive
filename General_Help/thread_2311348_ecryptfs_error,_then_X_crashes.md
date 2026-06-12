---
title: "ecryptfs error, then X crashes"
date: 2016-01-26
forum: General Help
---

### Post by ErroneousBosch on 2016-01-26
Ubuntu Gnome 15.10

This is happening every few hours. I can't seem to find a simple trigger. Been trying to get a picture of the error message but am never fast enough with the camera:

I am working happily along, suddenly my screen blacks, audio continues on for a few seconds, then I get an ecryptfs error, something about it trying to write to a newer file, and X restarts. I am forced to re-log in and restart everything.

What I am running at the time is generally Chrome, Nautilus with some SFTP connections, SublimeText 3, some terminal windows, and Pidgin.

Drivers are from the main repositories.

The only thing I can find in any log is in the x.org.log.old:

```

[ 60353.333] (EE) 
[ 60353.371] (EE) Backtrace:
[ 60353.407] (EE) 0: /usr/bin/X (xorg_backtrace+0x4e) [0x5616c055268e]
[ 60353.407] (EE) 1: /usr/bin/X (0x5616c039e000+0x1b89f9) [0x5616c05569f9]
[ 60353.407] (EE) 2: /lib/x86_64-linux-gnu/libc.so.6 (0x7f7d32c67000+0x352f0) [0x7f7d32c9c2f0]
[ 60353.407] (EE) 3: /usr/lib/xorg/modules/drivers/intel_drv.so (0x7f7d2f03d000+0x262da) [0x7f7d2f0632da]
[ 60353.407] (EE) 4: /usr/lib/xorg/modules/drivers/intel_drv.so (0x7f7d2f03d000+0x2b631) [0x7f7d2f068631]
[ 60353.407] (EE) 5: /usr/lib/xorg/modules/drivers/intel_drv.so (0x7f7d2f03d000+0x2d8d0) [0x7f7d2f06a8d0]
[ 60353.407] (EE) 6: /usr/lib/xorg/modules/drivers/intel_drv.so (0x7f7d2f03d000+0x636c4) [0x7f7d2f0a06c4]
[ 60353.407] (EE) 7: /usr/lib/xorg/modules/drivers/intel_drv.so (0x7f7d2f03d000+0xf51a7) [0x7f7d2f1321a7]
[ 60353.407] (EE) 8: /usr/lib/xorg/modules/drivers/intel_drv.so (0x7f7d2f03d000+0x104a27) [0x7f7d2f141a27]
[ 60353.407] (EE) 9: /usr/bin/X (0x5616c039e000+0x185c2c) [0x5616c0523c2c]
[ 60353.407] (EE) 10: /usr/bin/X (DRI2CopyRegion+0x8e) [0x5616c052434e]
[ 60353.407] (EE) 11: /usr/bin/X (0x5616c039e000+0x188723) [0x5616c0526723]
[ 60353.407] (EE) 12: /usr/bin/X (0x5616c039e000+0x5818f) [0x5616c03f618f]
[ 60353.407] (EE) 13: /usr/bin/X (0x5616c039e000+0x5c34b) [0x5616c03fa34b]
[ 60353.407] (EE) 14: /lib/x86_64-linux-gnu/libc.so.6 (__libc_start_main+0xf0) [0x7f7d32c87a40]
[ 60353.408] (EE) 15: /usr/bin/X (_start+0x29) [0x5616c03e46c9]
[ 60353.408] (EE) 
[ 60353.411] (EE) Segmentation fault at address 0x0
[ 60353.411] (EE) 
Fatal server error:
[ 60353.411] (EE) Caught signal 11 (Segmentation fault). Server aborting
[ 60353.411] (EE) 
[ 60353.413] (EE) 
Please consult the The X.Org Foundation support 
	 at http://wiki.x.org
 for help. 
[ 60353.413] (EE) Please also check the log file at "/var/log/Xorg.0.log" for additional information.
[ 60353.413] (EE) 
[ 60353.478] (II) AIGLX: Suspending AIGLX clients for VT switch
[ 60354.699] (EE) Server terminated with error (1). Closing log file.


```

Halp?

---

### Post by ErroneousBosch on 2016-01-27
Switched Video drivers to the OIBAF drivers and this problem seems solved.

---

