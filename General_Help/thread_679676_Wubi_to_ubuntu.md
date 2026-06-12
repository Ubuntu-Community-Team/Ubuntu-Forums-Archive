---
title: "Wubi to ubuntu"
date: 2008-01-27
forum: General Help
---

### Post by sunzaru on 2008-01-27
i installed Wubi, got all the patches/udpates.  got LVPM and converted to a real install  YAAAY.  Tested it out for a bit longer.. booted into windows and uninstalled wubi, formated that partition to ext3 to use as another mount (not sure if thats the right name.. w/e.  it's mounted and all hunky doory. but... when i do

```

sudo mount -a
[code]

i get this
[code]
Failed to access '/dev/disk/by-uuid/CAECAC9BECAC82F5': No such file or directory

```

i'm GUESSING that's where the wubi version of the install was and since i deleted it.. it cant mount it.  i'm goign to remove that from my fstab but figured it might be usefull to have someone see this.  now to edit grub so i dont have so many boot options
ubuntu 2.6.20-16-generic
ubuntu 2.6.20-16-generic safe mode (i think)
ubuntu 2.6.20-14-generic (i think)
ubuntu 2.6.20-14-generic safe mode (i think)
mem test.. (prolly leave that in)
windows
windows xp pro
other...

<3 the wubi installer though.  for whatever reason ubuntu didn't like using my dvd drive as a boot drive (and it's the only one i have).  may have taken longer but.. i remember redhat 7 and oops... formated the wrong drive.. oh NOS!

---

### Post by K.Mandla on 2008-01-27
Moved to Wubi subforum.

---

### Post by ago on 2008-01-28
> **sunzaru said:**
> 
i'm GUESSING that's where the wubi version of the install was and since i deleted it.. it cant mount it.  i'm goign to remove that from my fstab but figured it might be usefull to have someone see this.

Correct

---

