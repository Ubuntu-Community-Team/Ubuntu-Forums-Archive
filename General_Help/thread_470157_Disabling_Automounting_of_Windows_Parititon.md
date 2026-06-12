---
title: "Disabling Automounting of Windows Parititon"
date: 2007-06-10
forum: General Help
---

### Post by DerangedDingo on 2007-06-10
Hello... 
I'm having a really noobish problem and it's getting on my nerves
I tried searching too, but my problem is sort of specific to my computer

A) Before I changed anything, if I tried to unmount my NTFS partition (/dev/sda2) it would say that it disagreed with my /etc/fstab and therefore could not unmount my partition. How can I fix this?

B) How can I just stop the automounting in general, so, if I ever need anything, I could mount it manually?


PS: In desperation, I backed up my /etc/fstab and then erased the entry for my windows partition. this changed nothing, and made it more impossible to unmount the volume. I'll change it back to normal in a second.

Thank you!

---

### Post by scott_g on 2007-06-11
If you try removing the entry from your fstab file, then rebooting your computer (should unmount the drive), it shouldnt remount it.   I think ubuntu only reads the fstab file on boot (I think).  Unless I've missunderstood the problem.

Scott

---

### Post by merlinus on 2007-06-11
You need to unmount the drive as root.

```

sudo umount /media/hda1

```

as an example.

You might try adding noauto to the appropriate lines in /etc/fstab, but back it up first!

-merlin

---

### Post by DerangedDingo on 2007-06-12
thanks, that worked merlinus.. but i thought i was unmounting as root, because it would ask for an administrator password most of the time.
oh well. i'm prolly getting it confused with something else.
Thanks!

---

