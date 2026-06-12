---
title: "Mounting FAT32 partition from livecd for read/write"
date: 2007-03-21
forum: General Help
---

### Post by ConCor on 2007-03-21
Hello,

I'm running Xubuntu 6.10 off of a livecd. I would like to mount my primary partition (FAT32) for read/write operations, but I'm having some difficulty. I can mount it for read access, and root can write to it, but I'd like to be able to do things without running as root or prefacing every command with "sudo." ;) I'm fairly new to Linux, and I can't figure out how to perform the correct permissions changes.

Any help would be appreciated, thanks.

---

### Post by taurus on 2007-03-21
Assuming it's /dev/hda1, run these from a terminal

```
sudo mkdir /media/windows
sudo mount -t vfat /dev/hda1 /media/windows -o iocharset=utf8,umask=000
df -h
```

---

### Post by ConCor on 2007-03-21
I'm impressed by your speed. ;)

Thank you very much, this worked perfectly. Cheers, taurus!

---

### Post by taurus on 2007-03-21
I can only type as fast as my fingers can move.  ;) 

And you're welcome.

---

### Post by hikaricore on 2007-03-21
it's no wonder taurus has over 13k posts :P

---

### Post by taurus on 2007-03-21
> **hikaricore said:**
> it's no wonder taurus has over 13k posts :P

You should check out the second line of my sig!  :-$

---

### Post by hikaricore on 2007-03-21
> **taurus said:**
> You should check out the second line of my sig!  :-$

I still can't quite manage to think of beans as posts.

The beans I remember make the night disappear and usually end up getting my roomies arrested.


rofl

---

### Post by taurus on 2007-03-21
> **hikaricore said:**
> 
The beans I remember make the night disappear and usually end up getting my roomies arrested.

rofl

#-o

---

