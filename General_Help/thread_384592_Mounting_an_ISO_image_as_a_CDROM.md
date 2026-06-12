---
title: "Mounting an ISO image as a CDROM?"
date: 2007-03-14
forum: General Help
---

### Post by johann_p on 2007-03-14
I have an ISO image for a CD on my harddisk and I *could* burn it on a CD, then put it into my CDROM drive and mount it. 

But is it possible to mount the ISO image directly so that it looks like a physical CDROM in the CDROM drive to the OS?

---

### Post by llamakc on 2007-03-14
Yeah, you can mount an iso, but what is it you want the operating system to do with it? Just browse it/copy stuff?

sudo mount -o loop /path/to/image.iso /path/to/mount/point

---

### Post by johann_p on 2007-03-14
> **llamakc said:**
> Yeah, you can mount an iso, but what is it you want the operating system to do with it? Just browse it/copy stuff?

sudo mount -o loop /path/to/image.iso /path/to/mount/point

Thank you that works great! I just need to read from the files from time to time.

I have added the following line to /etc/fstab - will this be the correct way to mount the ISO at boot time?
```

/path/to/isofile.iso  /mnt/dvd  udf  ro,loop=/dev/loop0 0 0

```

---

### Post by llamakc on 2007-03-14
I've never bothered to specify which loop device. Try it. Unmount the iso that you manually mounted:

sudo umount /path/to/mount/point

Add that to /etc/fstab and run

sudo mount -a

---

### Post by johann_p on 2007-03-14
> **llamakc said:**
> I've never bothered to specify which loop device. Try it. Unmount the iso that you manually mounted:

sudo umount /path/to/mount/point

Add that to /etc/fstab and run

sudo mount -a

Thanks again - everything works great that way.

---

