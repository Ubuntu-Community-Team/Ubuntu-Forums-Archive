---
title: "Vista hibernation problem"
date: 2007-11-14
forum: General Help
---

### Post by M4NIC on 2007-11-14
Hello all, new user of ubuntu here, very happy up to now, although I have a small problem..

My system is a Toshiba satellite pro u200 laptop, and I have a dual boot (using grub) with Vista configuration. The marriage seemed to be going fine, until I hibernated Vista.

When vista is hibernated and I load Ubuntu, Ubuntu cant access the ntfs drives! its like theyre locked by vista because its hibernated, Also, right after I select ubuntu is the grub menu, I get an error that something (probably the disks) could not be loaded. This only happens when Vista is hibernated, otherwise ubuntu sees the disks perfectly. 

This problem has also been reported here: [http://ubuntuforums.org/showthread.php?p=3772303#post3772303]("http://ubuntuforums.org/showthread.php?p=3772303#post3772303")

Another problem I have is that sometimes I cant see the grub menu, as the toshiba splashscreen stays until you blindly select something and press enter...

anw the hibernation issue is more important to me, if anyone knows a workaround please tell :)

---

### Post by njparton on 2007-11-14
Shutdown vista before tyring to access the ntfs drives.

I would have thought it would have only locked open files, not the whole drive, but hey, if you're not using it just shut it down and reboot into linux.

That way you'll also save on resources such as hard drive space and/or ram too :)

---

### Post by M4NIC on 2007-11-16
The thing is, most of the time vista is hibernated as Im constantly on the run and need my battery.

A suggestion from a friend was that I had the Vista booter first and then Grub. But what happens with the hibernated content?

---

