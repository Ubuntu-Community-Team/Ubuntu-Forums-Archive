---
title: "Failing to compile modules with rt-kernel"
date: 2006-12-02
forum: General Help
---

### Post by The Soundophiliac on 2006-12-02
I'm using the ubuntumusique realtime kernel for edgy. I've been trying to compile dvb-usb but have failed. 

I get the following error trying to load a module:

```
WARNING: Error inserting dvb_core (/lib/modules/2.6.17.6-rt7-ubuntumusique/kernel/drivers/media/dvb/dvb-core/dvb-core.ko): Invalid module format
FATAL: Error inserting dvb_usb (/lib/modules/2.6.17.6-rt7-ubuntumusique/kernel/drivers/media/dvb/dvb-usb/dvb-usb.ko): Invalid module format

```

dmesg says the following:
```
[50631.073000] dvb_core: version magic '2.6.17.6-rt7-ubuntumusique preempt mod_unload 486 gcc-4.1' should be '2.6.17.6-rt7-ubuntumusique preempt mod_unload 486 gcc-4.0'
[50631.083000] dvb_usb: version magic '2.6.17.6-rt7-ubuntumusique preempt mod_unload 486 gcc-4.1' should be '2.6.17.6-rt7-ubuntumusique preempt mod_unload 486 gcc-4.0'
[50885.174000] dvb_core: version magic '2.6.17.6-rt7-ubuntumusique preempt mod_unload 486 gcc-4.1' should be '2.6.17.6-rt7-ubuntumusique preempt mod_unload 486 gcc-4.0'
[50885.190000] dvb_usb: version magic '2.6.17.6-rt7-ubuntumusique preempt mod_unload 486 gcc-4.1' should be '2.6.17.6-rt7-ubuntumusique preempt mod_unload 486 gcc-4.0'

```

I've tried compiling with numerous CC= options such as CC=gcc-4.0 (don't if that makes any sense, though). The problem seems to be that the modules' version magic info doesn't match that of the kernel.

Compiling my own rt-kernel is not an option since I can't get them to boot for some reason. 

Is there any solution?

Thanks

---

### Post by The Soundophiliac on 2006-12-04
Bump.

---

