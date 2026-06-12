---
title: "Need help working with live cd"
date: 2007-04-07
forum: General Help
---

### Post by disturbedite on 2007-04-07
ok, i'm asking this here as an insurance policy.  (please see my [other thread]("http://ubuntuforums.org/showthread.php?t=403083") for more info on the situation).   i'm gonna be direct and to the point.

i screwed up my fstab, but it is correctable.  the problem is, the part that is screwed up is the / partition/hdd.  i can't get into kubuntu or even a command prompt cuz bash isn't able to be located.  (obviously, since the / partition isn't accessible).

i couldn't get my edgy dvd to boot (drive won't recognize it) even with the only boot device set as the cd/dvd rom.  so the only live cd i could find (luckily!) was an old knoppix disc (3.3 beta).  so i boot with it, but the / partition is mounted read only!  so i can't edit my messed up fstab.

how do i do that?

i need to make the filesystem writable.  (thats all i have to do to be able to edit fstab right?  i can just run the root shell and it'll automatically allow me to write fstab since the owner is root in both cases right?  or is live cd automatically ran as root and i can just edit fstab in kate or another text editor?)

---

### Post by zvacet on 2007-04-07
Try from recovery mode.That will give you root privileges and you will be able to edit fstab.

---

### Post by disturbedite on 2007-04-07
uh, thanks for the suggestion, but no it won't.  it can't work cuz the / partition isn't accessible as i said.  (and thats the first thing i tried anyway).

---

### Post by disturbedite on 2007-04-07
UPDATE:
i finally figured it out.  it was easier than i initially realized.  apparently with knoppix (or at least up to version 3.3) your partitions are mounted read only.  i knew that already, as i mentioned above.  what i had to do was unmount my / partition and edit the live cd's fstab and  add rw to make it writable and then save it.  next i edited my fstab from my / partition and saved and reboot my pc and voila!  all fixed.  i certainly hope the kernel devs or ubuntu or whoever made the change fix this crap thats been going on.

---

