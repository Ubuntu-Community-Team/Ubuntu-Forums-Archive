---
title: "mount ~/Downloads to secondary HDD"
date: 2012-11-29
forum: General Help
---

### Post by Aeefire on 2012-11-29
Hey guys!

Following thing: I just setup a new dual boot system on my fresh SSD and now I want to have /home/*username*/Downloads mounted to my secondary (normal ntfs) hdd. 

What I tried was following thing in fstab:

```

/media/*username*/SecondaryHDD1/SharedDownloads /home/*username*/Downloads defaults bind 0 0
```

what I get is a "error on mounting" when i reboot. (or some similiar message).

What am I doing wrong? might it be due to different filesystems? i am a bit clueless... thanks in advance :)

---

### Post by nothingspecial on 2012-11-29
Is your external hard drive specified in fstab above your bind ?

---

### Post by Aeefire on 2012-11-29
nope it isn't, but it seems to get automatically mounted (was connect during installation).. so do i still need to mount it inside fstab?

---

### Post by nothingspecial on 2012-11-29
Well fstab is read at boot,  the external drive automounts when you log in.

You need to list the external drive  in fstab first.

---

### Post by Aeefire on 2012-11-29
did it again (probably without typo this time) and now it works! thanks again :D

---

