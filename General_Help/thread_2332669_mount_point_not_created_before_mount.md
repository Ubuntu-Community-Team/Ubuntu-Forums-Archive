---
title: "mount point not created before mount??"
date: 2016-08-02
forum: General Help
---

### Post by jfaberna on 2016-08-02
I use to do the following:

```

mkdir /media/recordedtv
mount /dev/sdd1 /media/recordedtv

```

The other day on mythbuntu 14.04.4, I forgot to make the subdir in media.  When the system booted the mount was in /etc/fstab and it mounted in /media/recordedtv as I wanted even though I didn't create the directory ahead of time.

Did I miss something or does that requirement not exist anymore??

---

### Post by Dennis N on 2016-08-03
If you mount a partition using an entry in /etc/fstab, you don't need to create the mount point directory yourself - it will be automatically created if not present and remains there until removed. I have been doing this when setting up a separate data partition on a new system ever since I discovered it by accident (as you just did) a couple of years ago. But, in other mount situations you do need to create the directory first.

---

### Post by jfaberna on 2016-08-03
> **Dennis N said:**
> If you mount a partition using an entry in /etc/fstab, you don't need to create the mount point directory yourself - it will be automatically created if not present and remains there until removed. I have been doing this when setting up a separate data partition on a new system ever since I discovered it by accident (as you just did) a couple of years ago. But, in other mount situations you do need to create the directory first.

thanks, that's a relief.  didn't know if I was lucky or forgetful.  We retired computer geeks never know which it is.:)

---

