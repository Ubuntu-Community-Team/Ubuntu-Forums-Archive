---
title: "localhost kernel: general protection fault ???"
date: 2005-03-24
forum: General Help
---

### Post by negatory on 2005-03-24
I'm with Hoary amd64 version and I've just got this on a console:

Message from syslogd@localhost at Thu Mar 24 20:02:34 2005 ...
localhost kernel: general protection fault: 0000 [1]

What's this all about?It didn't hang my computer or anything it just said that.
My tail -n 15 /var/log/messages follows:

root@matrix:~ # tail -n 15 /var/log/messages
Mar 24 20:02:34 localhost kernel: CR2: 0000050120000238 CR3: 0000000000101000 CR4: 00000000000006e0
Mar 24 20:02:34 localhost kernel: Process scsi_eh_4 (pid: 8616, threadinfo 00000100223b6000, task 00000100219bc370)
Mar 24 20:02:34 localhost kernel: Stack: 00000100223b7d58 ffffffff802a799c 0000000000000000 0000000b0000000e
Mar 24 20:02:34 localhost kernel:        000006d400000034 0000026d00030001 0e45028f100e4200 0e42200e45038e18
Mar 24 20:02:34 localhost kernel:        058c0686300e4128 400e44380e44048d
Mar 24 20:02:34 localhost kernel: Call Trace:<ffffffff8010e6a1>{error_exit+0} <ffffffffa07231e4>{:usb_storage:bus_reset+51}
Mar 24 20:02:34 localhost kernel:        <ffffffffa00389f2>{:scsi_mod:scsi_try_bus_reset+108}
Mar 24 20:02:34 localhost kernel:        <ffffffffa0038b8b>{:scsi_mod:scsi_eh_bus_reset+149}
Mar 24 20:02:34 localhost kernel:        <ffffffffa003905a>{:scsi_mod:scsi_eh_ready_devs+54}
Mar 24 20:02:34 localhost kernel:        <ffffffffa0039314>{:scsi_mod:scsi_unjam_host+416} <ffffffffa003943a>{:scsi_mod:scsi_error_handler+269}
Mar 24 20:02:34 localhost kernel:        <ffffffff80129e83>{schedule_tail+11} <ffffffff8010e857>{child_rip+8}
Mar 24 20:02:34 localhost kernel:        <ffffffffa003932d>{:scsi_mod:scsi_error_handler+0}
Mar 24 20:02:34 localhost kernel:        <ffffffff8010e84f>{child_rip+0}
Mar 24 20:02:34 localhost kernel:
Mar 24 20:02:34 localhost kernel: Code: 48 8b 14 06 f6 c2 01 0f 84 da fc ff ff 48 89 e8 48 21 ca 48

Any ideas?
Thanks
Pedro Carrico

---

### Post by alastair on 2005-03-24
Kernel bug? Hard to say.
Looks like there might be a problem with the USB subsystem? Do you have USB devices attached?

You'd be best to do some digging around on the net and see if you can find similar/same problems.

---

### Post by negatory on 2005-03-24
Maybe it appened when I switched on my printer (HP PSC 1350).I've googled it up but no luck...diferent reasons apeared and strange kernel bugs but from what I've read some of them ended with a system hang.Well my system runs fine and I can't reproduce it again...
Hope it doesn't give me some nightmares...
Pedro Carrico

---

