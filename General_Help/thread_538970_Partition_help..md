---
title: "Partition help."
date: 2007-08-30
forum: General Help
---

### Post by bittiez on 2007-08-30
Hi, when i installed windows i made two partitions, one for windows and one for my storage, well i reformatted and set the system to ext3 for the windows partition and installed ubuntu, but now I cant seem to edit, chance, add, remove etc anything in my storage partition, its owner is root, and I would like to change that, I did chown, chgrp, chmod 777 and nothing works, they all tell me its a read only thing..(Yes I was in root through sudo -i)

Just so you know im a complete noob to ubuntu.

---

### Post by nitro_n2o on 2007-08-30
what is exactly your storage FS?

---

### Post by merlinus on 2007-08-30
My guess is your storage is NTFS.  If so, then install the drivers and configure it:

```

sudo apt-get install ntfs-config

```

then:

```

sudo ntfs-config

```Tick the appropriate boxes and restart.

-merlin

---

### Post by bittiez on 2007-08-30
> **merlinus said:**
> My guess is your storage is NTFS.  If so, then install the drivers and configure it:

```

sudo apt-get install ntfs-config

```

then:

```

sudo ntfs-config

```Tick the appropriate boxes and restart.

-merlin

Thank you thank you thank you!!! It works just fine now :)

---

### Post by merlinus on 2007-08-30
You are most welcome.  Glad I could help.

-merlin

---

### Post by ewloe on 2007-08-30
I had given up hope of getting mine to work to but this did it perfectly thank you

---

### Post by merlinus on 2007-08-30
Yeah, ewloe, I remember some of your previous posts, but others had already tried to help so I stayed out of it.

Glad it worked!

-merlin

---

