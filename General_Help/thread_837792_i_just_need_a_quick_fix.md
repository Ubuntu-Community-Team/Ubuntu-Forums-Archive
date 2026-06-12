---
title: "i just need a quick fix"
date: 2008-06-22
forum: General Help
---

### Post by n8makar on 2008-06-22
i've searched and read about using grub to boot windows from another hdd, but i haven't been successful so far. i have opensuse,fedora, and ubuntu on my sata master (hd0) and windows xp and vista on my ide slave (hd1).title Windows

```
title Windows XP
map (hd0) (hd1)
map (hd1) (hd0)
root (hd1,0)
chainloader +1

```

and

```
title Windows Vista
map (hd0) (hd1)
map (hd1) (hd0)
rootnoverify (hd1,1)
chainloader +1

```

for both vista and xp in grub. for some reason (i dont know if this set up caused it) my xp partition was suddenly ruined. unreadable and unusable. reinstall and now up and running again.

all i need is the correct way to add both windows vista and xp to the grub boot loader and boot correctly.

---

### Post by n8makar on 2008-06-22
nevermind i got it working somehow

---

