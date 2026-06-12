---
title: "Partition help"
date: 2006-11-05
forum: General Help
---

### Post by glaeven on 2006-11-05
Ok, i am running edgy (6.10) on an old machine. the HDD is total of about 30gb. I had to create a new partition b/c dapper was still good, and edgy was needed. so, dapper died, and i deleted it, but when i installed edgy, i made a mistake. instead of giving edgy the most space, i gave it to dapper, and edgy got only 3gb. no, i have 23gb of unallocated space, and i dont know how to expand edgy into that

any ideas? :confused:

---

### Post by boban on 2006-11-05
You can try gparted (gnome partition editor)
```

sudo aptitude install gparted

```

After installation run System->Administration->Gnome Partition Editor.

---

### Post by Sef on 2006-11-07
You can't partition a mounted hard drive.  Better is download and burn [GParted]("http://gparted.sourceforge.net/").

---

### Post by boban on 2006-11-07
> **Sef said:**
> You can't partition a mounted hard drive.  Better is download and burn [GParted]("http://gparted.sourceforge.net/").

That's right... I didn't think about that... But as far as I remember - gparted is available on Ubuntu livecd too, so no need to download anything if he has livecd available.

---

### Post by Sef on 2006-11-07
> That's right... I didn't think about that... But as far as I remember - gparted is available on Ubuntu livecd.

True, but GParted's Live CD is more up to date.

---

### Post by boban on 2006-11-07
> **Sef said:**
> True, but GParted's Live CD is more up to date.

Ok Glaeven, he has a good point there... Forget what I said, Sef has a better answer then me :)

---

