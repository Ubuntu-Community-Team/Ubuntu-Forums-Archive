---
title: "SD Card won't mount - options error"
date: 2008-02-10
forum: General Help
---

### Post by hops on 2008-02-10
I mounted a micro SD card in an adapter and it came up read only.  I then tried to change the options using the properties gui settings panel.  The result was that I screwed up mount options and now the card won't mount due to errors in mount options.  Since the mount fails the card does not appear is fstab and I have no idea  of where to go to correct the mount options.

Also, I thought that I posted this yesterday, but I can't find it, so I am assuming it never got posted.

---

### Post by paultag on 2008-02-10
can you mount it manually?

give this a shot:

```

mkdir /mnt/SD
mount /dev/<SD CARD> /mnt/SD


```

where <SD CARD> is the /dev/ name for the card. Should be something along the lines of /dev/sdX.

---

