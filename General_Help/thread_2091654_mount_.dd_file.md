---
title: "mount .dd file"
date: 2012-12-05
forum: General Help
---

### Post by Lokikol on 2012-12-05
Hello Guys,

I'm pretty new to Ubuntu and Linux Shell and I have a question. 

I've got a .dd file, which is a harddrive. I want to mount it so what I want to do is the following:

```

losetup -o $((63*512)) /dev/loop0 file.dd
mount /dev/loop0 /mnt

```

The first step works, but on the mount I got the following Error:

fuse: mount failed: No Permission.

The HD is a Windows XP Harddrive and somewhere else it tells me that the .dd I've got only read-rights on the .dd, but no write-rights. I think that could be the problem. But I don't know how to get the right to write. 

Thanks
Loki

---

### Post by rnerwein on 2012-12-06
> **Lokikol said:**
> Hello Guys,

I'm pretty new to Ubuntu and Linux Shell and I have a question. 

I've got a .dd file, which is a harddrive. I want to mount it so what I want to do is the following:

```

losetup -o $((63*512)) /dev/loop0 file.dd
mount /dev/loop0 /mnt

```The first step works, but on the mount I got the following Error:

fuse: mount failed: No Permission.

The HD is a Windows XP Harddrive and somewhere else it tells me that the .dd I've got only read-rights on the .dd, but no write-rights. I think that could be the problem. But I don't know how to get the right to write. 

Thanks
Loki
i think you must be super-user to work with "mount"

---> sudo mount /dev/loop0 /mnt

cheers

---

