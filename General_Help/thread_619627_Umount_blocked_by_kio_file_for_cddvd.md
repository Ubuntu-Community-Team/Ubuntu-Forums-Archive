---
title: "Umount blocked by kio_file for cd/dvd"
date: 2007-11-21
forum: General Help
---

### Post by brel on 2007-11-21
I can't eject a cd/dvd even doing an 'sudo eject'. The error I get is:

mount: /media/cdrom0: device is busy
umount: /media/cdrom0: device is busy

In 'dolphin' I get a bit more info: it tells me kio_file has locked the device. After killing the kio_file processes listed in the error msg, I could eject the disc, but that's a lot of work to get a disk out of the drive :)

Incidentally, unmounting also does not work for my usb keys. I get a similar msg: device in use. I end up just pulling out the key and have so far had no problems with data loss but I'd do a proper remove if I could.

Everything worked fine in feisty fawn. I've upgraded to gutsy and I suspect 'dolphin' (the new kde file mgr).

Other details of interest: 64bit, kubuntu. I've changed nothing in the confs.

Thanks

---

