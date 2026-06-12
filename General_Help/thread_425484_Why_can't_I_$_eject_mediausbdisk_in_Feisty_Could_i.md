---
title: "Why can't I $ eject /media/usbdisk in Feisty? Could in Edgy..."
date: 2007-04-27
forum: General Help
---

### Post by kwaanens on 2007-04-27
$ eject /media/E10/
umount: /media/E10 is not in the fstab (and you are not root)
eject: unmount of `/media/E10' failed
~$ umount /media/E10 
umount: /media/E10 is not in the fstab (and you are not root)

/media/E10 being my automatically mounted iRiver E10.
Right clicking and "unmount media" works, but that's not good enough. I have "eject /media/E10" in s a script, and need it to work.

- Ketil

---

### Post by mac.ryan on 2007-04-27
Does "sudo eject/umount" make the trick? if yes, then check if your drive has been mounted with the "nouser" option.

However, check launchpad... there are several reported (confirmed) bugs with USB mounting/unmounting, and also some workarounds.

The last thing coming to my mind is that if you have beagle set to index also your removable drives, then it will be preventing them to be unmounted (even if the indexing is not going on at the moment you want to umount).

---

### Post by kwaanens on 2007-05-01
Yes, sudoing does the trick. I'll check launchpad. Do you have any direct links?

Thanks!

- Ketil

---

### Post by mac.ryan on 2007-05-01
> **kwaanens said:**
> Do you have any direct links?

Sorry, I didn't keep the link to the one I saw... yet, you will be astonished by the amount of reported bugs in this area!!! :-/

Happy the sudo thing worked for you, anyhow!

---

### Post by kwaanens on 2007-05-01
> **mac.ryan said:**
> Sorry, I didn't keep the link to the one I saw... yet, you will be astonished by the amount of reported bugs in this area!!! :-/

I browsed launchpad, didn't find anything that fit, so I made a new bug report. [https://bugs.launchpad.net/ubuntu/+source/eject/+bug/111541](https://bugs.launchpad.net/ubuntu/+source/eject/+bug/111541)

> **mac.ryan said:**
> Happy the sudo thing worked for you, anyhow!

Actually, sudo isn't really an option. The reason I need eject is because I use it from inside a script, and I don't want/ need users to sudo when using the script.

So, seing that unmounting works for ordinary users in Nautilus, I'm better off using that "solution" for now.

- Ketil

---

