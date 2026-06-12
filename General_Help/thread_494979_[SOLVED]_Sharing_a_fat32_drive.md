---
title: "[SOLVED] Sharing a fat32 drive"
date: 2007-07-07
forum: General Help
---

### Post by letubenaiah on 2007-07-07
I'd posted this question over in the Networking forum but no one had an answer so I though I'd try over here.

I've got a ubuntu partition formated fat32 that I want to be able to write to from my windows virtual machine. I can see the files from Windows but they are read only and I can't write to that drive from the windows VM. I can write to it from ubuntu. When I right click on the drive and go to permissions it lets me change the options but then it changes them right back. What do I need to do to fix this?

Thanks,

Benaiah

---

### Post by orb9220 on 2007-07-07
What is the fstab entry for the fat32 drive? Post it here

---

### Post by letubenaiah on 2007-07-07
Heres the fstab entry for it.

```

 /dev/sda1 /audio vfat defaults,rw,exec,uid=1000,gid=1000,auto 0 0

```

---

### Post by orb9220 on 2007-07-08
/dev/sda1 /audio vfat defaults,rw,exec,uid=1000,gid=1000,auto 0 0

try

 /dev/sda1 /audio vfat iocharset=utf8,umask=000 0 0

or

[http://www.ubuntugeek.com/widows-ntfs-partitions-readwrite-support-made-easy-in-ubuntu-feisty.html](http://www.ubuntugeek.com/widows-ntfs-partitions-readwrite-support-made-easy-in-ubuntu-feisty.html)

---

### Post by letubenaiah on 2007-07-08
I tried changing fstab to what you suggested but when I did that the partition would not mount.  The NTFS configuration tool didn't work either, but this is a fat32 partition so is it supposed to work on that as well?  

Thanks, Benaiah

---

### Post by logos34 on 2007-07-08
what about

**sudo chown -R user:user /audio**   (*where 'user'=your username)
**sudo chmod -R 755 /audio**

does that help?

add: ntfs config is for adding write capability to NTFS only.  You can read+write to fat32 natively

---

