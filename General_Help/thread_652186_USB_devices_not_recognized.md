---
title: "USB devices not recognized"
date: 2007-12-28
forum: General Help
---

### Post by javi0084 on 2007-12-28
When Ubuntu 7.10 is running and I plug in a USB device, it wont recognize it. Mouse, thumb drive, MP3 player, nothing. They don't even light up. But if I leave it plugged in and reboot, they show up.

I believe it has something to do with noapic option being on GRUB. I remember reading somewhere on here that some one had to take it off to get hotplugging USB devices to work again but when I remove it, Ubuntu wont load. I read this thread: [http://ubuntuforums.org/showthread.php?t=146783](http://ubuntuforums.org/showthread.php?t=146783) but I still can't get it to work.

Any ideas? Thanks!

---

### Post by javi0084 on 2008-01-02
Anyone? Maybe?

---

### Post by javi0084 on 2008-01-04
It would be nice to be able to plug in a USB device w/o having to reboot.

---

### Post by javi0084 on 2008-01-08
Its sad that I had to reinstall..... *sigh* .....Vista. :(

---

### Post by freddyp on 2008-01-08
Not to insult, but have you checked:

System>Preferences>Storage Tab and made sure the following is checked:

Mount removable drives when hot-plugged
Mount removable media when inserted
Browse removable media when inserted

Don't ask me how I know how easy it is to accidentally uncheck one.  This should ensure that the USB drive is being recognized by Ubuntu on insert, but remember if you don't ask the O/S to automount it, then it won't be automounted.

There are several threads on this topic.  hvae you tried a search in the forum for other ideas?

---

