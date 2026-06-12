---
title: "Getting 'not cleanly unumounted' on root disk on every reboot..despite 'shutdown -h'"
date: 2013-05-30
forum: General Help
---

### Post by onlinespending on 2013-05-30
I installed Ubuntu Server 13.04 on a USB thumb drive and every time I restart the machine it claims that the root partition was not cleanly unmounted. This is despite doing a graceful shutdown using something like 'shutdown -h 1' and waiting for the system to completely shutdown. The root filesystem is formated as ext2 (due to the fact that it's installed on a flash drive and I don't want the overhead or the excessive writes of the newer journaling filesystems) with noatime. I'm not sure if this somehow affects things. Here's its fstab entry.
```

UUID=16af12c7-953c-43b7-bd75-62432f730f91 /               ext2    noatime,errors=remount-ro 0       1
```

Any idea why this is happening or suggestions on how to prevent it? Thank you!

---

### Post by Bashing-om on 2013-05-30
[COLOR=#000000]onlinespending; Hi !
Just a shot while I am passing by.
I do not know that the ext2 format supports "hot plugging/unplugging" requiring a gvfs-mount to do so ( recognize an external device) .
Another thought, maybe the gvfs package is not installed on your system, I do not have it on one of my boxes and I MUST unmount external devices manually on that box.
The "mount" command will indicate if gvfs is available on your system.

Might I offer that you run 'buntu's file system check on that drive, then
go through the hassle (hope you are present) to manually unmount the device prior to halting. 
Do that a few times and see if that method prevents an unclean unmount. (???)
[/COLOR][INDENT][COLOR=#000000]
progress since ext2 -> lots change 

[/COLOR][/INDENT]

---

