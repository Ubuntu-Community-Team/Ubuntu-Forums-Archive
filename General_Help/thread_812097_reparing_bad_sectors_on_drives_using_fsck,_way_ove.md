---
title: "reparing bad sectors on drives using fsck, way over my head"
date: 2008-05-29
forum: General Help
---

### Post by garethsimpsonuk on 2008-05-29
Greetings ppl I really hope someone can help me, I posted in the server board but it's dead and I'm sat here twiddling my thumbs till i can get an answer.
Below is the last post which pretty much sums up where I've got to but you can read the rest here:

[http://ubuntuforums.org/showthread.php?t=811947]("http://ubuntuforums.org/showthread.php?t=811947")

I'm trying to repair bad secotrs ( i think that's what they are ) on a hard disk. Here is the last post


i read the man

i ran fsck -a /dev/sdb

fsck.ext2: bad magic number in super-block while trying to open /dev/sdb
/dev/sdb:
the superblock could not be read or does not describe a correct ext2 filesystem. if the device is valid and it really contains an ext2 filesystem ( it's ext3 ), then the superblock is corrupt, and you might try running e2fsck with an alternative superblock

so...

sudo e2fsck -b 8193 /dev/sdb

device or resource busy while trying to open /dev/sdb
Filesystem mounted or opened exclusively by another program?

What do I do here? it's not mountes as far as i'm aware..

plz help oh wonderful ubuntu gods

---

### Post by logos34 on 2008-05-29
did you try running the second command from a live cd?

---

### Post by garethsimpsonuk on 2008-05-29
what an excellent idea ill give it a go and thankyou for posting

---

### Post by paapereira on 2008-05-29
You can also unmount the drive

example:
```
umount /dev/sdb5
```

---

### Post by garethsimpsonuk on 2008-05-29
for some reason that didn't work, i cant remember the error msg

---

### Post by paapereira on 2008-05-29
Check [this]("http://lof-ubuntu-xp.blogspot.com/2008/04/error-while-starting-ubuntu.html").

I had a similar problem some time ago in my laptop, and I was able to fix it.

---

### Post by garethsimpsonuk on 2008-05-29
its a worth a shot thanx

---

### Post by garethsimpsonuk on 2008-05-29
for some reason a windows disc boots fine but when i try and boot from the ubuntu live cd i get a boot failure msg. n e ideas n e 1? im just ginna try the server cd first aswell ( by the way i have 2 self burnt cd's and 1 shipit cd and none of them work )

edit: v.strange, the server cd boots fine. is there anyway of getting a basich cmd shell from the install program?

---

