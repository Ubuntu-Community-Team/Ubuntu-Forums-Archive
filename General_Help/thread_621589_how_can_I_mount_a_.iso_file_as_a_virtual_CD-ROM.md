---
title: "how can I mount a .iso file as a virtual CD-ROM?"
date: 2007-11-23
forum: General Help
---

### Post by Diabolis on 2007-11-23
Is it possible to mount a .iso file and make it appear as a virtual CD-R drive? I think that if I'm able to accomplish this, then my windows installation under vmware will see those CDs too.

---

### Post by PeterJS on 2007-11-23
> **Diabolis said:**
> Is it possible to mount a .iso file and make it appear as a virtual CD-R drive? I think that if I'm able to accomplish this, then my windows installation under vmware will see those CDs too.

First VMware has options to mount iso, and it's probably best to use those.

However to answer your question:
```

sudo mount -t iso9660 something.iso /some/path

```

EDIT:

Yeah lzydb is right, that's what i get for doing things from memory and not trying them first.

---

### Post by lzydba on 2007-11-24
I was also searching for how to do this and came across this post.

I tried the above command and was met with an error message about the .iso not being a block device or something, So I did some more digging and found the following command that works:

```

sudo mount -o loop /path/to/something.iso /path/to/mountpoint

```

Hope that helps.

---

### Post by madjr on 2008-03-29
you can also mount isos with a gui using **gmount-iso** (in the repos or add/remove)

theres also:
[http://www.acetoneiso.netsons.org/viewpage.php?page_id=2](http://www.acetoneiso.netsons.org/viewpage.php?page_id=2)

---

