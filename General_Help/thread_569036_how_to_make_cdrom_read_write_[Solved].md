---
title: "how to make cdrom read write [Solved]"
date: 2007-10-06
forum: General Help
---

### Post by mhedges48 on 2007-10-06
Hello, I have put in a CD RW disk, and cannot write to it, only copy files from it to Ubuntu not from Ubuntu to CD. I have tried changing the ownership to me (root@user:/home/user# sudo chown user /media/cdrom0) and it says chown: changing ownership of `/media/cdrom0': Read-only file system

I've also tried to give me read write: sudo chmod -R ugo+rx /media/cdrom0, but the cd stays read only anything I do... 

Here is my fstab:
/dev/cdrom /media/cdrom0 udf,iso9660 user,noauto 0 0

any ideas?

thanks
matt

---

### Post by ryanVickers on 2007-10-06
You can't just "write" to a **compact disk** like a **universal serial bus** drive - you have to burn a disk - even if it's re-writable...

---

### Post by mhedges48 on 2007-10-06
Thanks!  I was going about this all wrong... downloaded gnomebake and all groovy...

---

### Post by ryanVickers on 2007-10-06
Yup, sounds about right! ;)

If you don't mind KDE apps, K3B is also **very good** (in my opinion, much better actually)!

---

### Post by mhedges48 on 2007-10-06
thanks again! i just installed it and will use it

---

