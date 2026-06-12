---
title: "Oracle 9i installation problems"
date: 2008-01-29
forum: General Help
---

### Post by bigb_thedestroyer on 2008-01-29
I'm trying to install Oracle 9i on to my Ubuntu (7.10) laptop and every time I run ```
./runInstall
``` I get the following error...

```
Initializing Java Virtual Machine from /tmp/OraInstall2008-01-29_08-10-42PM/jre/bin/java. Please wait...
Error occurred during initialization of VM
Unable to load native library: /tmp/OraInstall2008-01-29_08-10-42PM/jre/lib/i386/libjava.so: symbol __libc_wait, version GLIBC_2.0 not defined in file libc.so.6 with link time reference
```

I have also taken the advice of a post I saw in the forums and I moved into the install/linux/ directory of Disk 1 and tried to run the ./runInstall there.  I got the same error as above.  I looked into that directory : /tmp/OraInstall2008-01-29_08-10-42PM/jre/lib, and I could see the libjava.so.

I need assistance.  Could anyone point me in the right direction to help me get Oracle installed on my laptop.

Thanks,

Brian

---

