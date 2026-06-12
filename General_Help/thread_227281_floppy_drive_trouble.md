---
title: "floppy drive trouble"
date: 2006-08-01
forum: General Help
---

### Post by namelessone on 2006-08-01
This is a very multi-faceted question, so I hope i'm posting in the right place...

I recently found a copy of Pirates! Gold in the local thrift store and quickly bought it. I figured i could get it to install and run using dosbox even though it came on 3.5 floppy disks.

I didn't have a floppy drive installed, but I soon installed one, and added the following line to /etc/fstab:

```
/dev/fd0	/media/floppy0	vfat	user

```
(I also created a /media/floppy0 directory)

I inserted the first disk and tried to mount it and got the following message:

```
mount: block device /dev/fd0 is write-protected, mounting read-only

mount: /dev/fd0: can't read superblock
```

The first part about write-protection can be expected, but I don't understand the second part.

Does anyone know how to fix this problem?

---

### Post by apjone on 2006-08-01
how did you mount is??

---

### Post by namelessone on 2006-08-01
I tried mounting the drive twice. The first time by clicking on the floppy drive icon, and the second time by manually typing

```
sudo mount -t vfat /dev/fd0 /media/floppy0 
```

each time I got the same aforementioned error message.

I also noticed that if i don't put a disk in and I try to mount it, I get the same error message...now i am very very confused

---

### Post by apjone on 2006-08-02
did you put the IDE cable in the floppy drive correctly??

---

### Post by namelessone on 2006-08-02
Yes, I installed the drive correctly. The light turns on when I put a disk in.

---

### Post by blent07 on 2006-09-21
I'm having the same problem. Mine's an external USB Dell floppy drive. 

Anything anyone figured out about it?

---

