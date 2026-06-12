---
title: "I cannot do anything with audio CDs"
date: 2015-04-05
forum: General Help
---

### Post by ramicio on 2015-04-05
I don't even know where to start. Nothing will read them. Every program I try sees the drive as empty. If I insert a DVD I burned, containing just a bunch of files, and mount it, it works. I read something about some gvfs crap. I don't have a ~/.gvfs folder. I have gvfs installed. Where do I start? I am at my wit's end with this. This is on a server, so I don't have a desktop environment to go through system settings.

---

### Post by ian-weisser on 2015-04-05
> **ramicio said:**
> Every program I try sees the drive as empty.

What command-line-only audio CD programs have you tried?

---

### Post by ramicio on 2015-04-05
morituri, sound-juicer (x forwarding), and EAC via wine. morituri says it doesn't have permission for something, regardless of sudo.

---

### Post by ramicio on 2015-04-05
rip offset find

> Checking device /dev/cdrom
eject: unable to open `/dev/sr0'
rip: error: cannot read CD from drive.
cdrdao says:
Unable to open SCSI device /dev/cdrom: Permission denied.
Please use option '--device {[proto:]bus,id,lun}|device', e.g. --device 0,6,0, --device ATA:0,0,0 or --device /dev/cdrom
Cannot setup device /dev/cdrom.

---

### Post by ramicio on 2015-04-06
Nevermind. Working.

---

