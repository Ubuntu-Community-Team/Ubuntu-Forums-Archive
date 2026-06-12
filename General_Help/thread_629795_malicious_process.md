---
title: "malicious process"
date: 2007-12-02
forum: General Help
---

### Post by big_area on 2007-12-02
I noticed this process running as root after reading the "malicious commands" sticky

```
/bin/dd bs 1 if /proc/kmsg of /var/run/klogd/kmsg
```

which looks very similar to 
> Block device manipulation: Causes raw data to be written to a block device. Often times this will clobber the filesystem and cause total loss of data:

any_command > /dev/sda
dd if=something of=/dev/sda



could someone explain what this process is doing and/or if it is doing something that it shouldn't be?

thanks ahead of time

---

### Post by tact on 2007-12-02
Hey there,

That one is no malicious process so don't worry.  klogd is the kernel log daemon.

Its copying stuff from /proc to log.

Very alert of you to notice it.  The important thing in ...
any_command > /dev/sda
dd if=something of=/dev/sda

... is the "> /dev/sda" or "of = /dev/sda" part.  

Both statements are saying "write whatever was before the ">" or "of" to /dev/sda"   (/dev/sda being your first sata  HDD, likely your boot drive, and so overwriting your data on that drive - perhaps making your system unbootable later.)

---

