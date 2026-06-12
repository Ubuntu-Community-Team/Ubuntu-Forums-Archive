---
title: "No rewritable DVD media found.  Unable to format"
date: 2007-01-11
forum: General Help
---

### Post by mistypotato on 2007-01-11
No matter what program I use to try and format a DVD, it says.....

"No rewritable DVD media found, Unable to format"

Do anyone know how to resolve this?

Thanks if you do !!

---

### Post by meng on 2007-01-11
I understand reformating a DVD+/-RW is not recommended, it decreases the lifespan of the disc or something. Can't you just over-write the disk (with Nautilus burner, Gnomebaker or K3B) when you need too? Or does that give an error too?

---

### Post by mistypotato on 2007-01-11
Hi Meng!!

yes, it gives me the same error whether I'm trying to burn a DVD OR re-format it.
I just thought reformatting would solve the other problem :-(

---

### Post by mistypotato on 2007-01-11
I can "read" a DVD just fine.

And I've tried several different RW DVD's

They actually have the RW on them ;)

---

### Post by meng on 2007-01-11
Ok thanks for clarifying. I think the issue must be that your DVD drive isn't recognized as a writer, or at least not as a rewriter.

---

### Post by mistypotato on 2007-01-11
Wait a minute........

I have a "Broken Link"

Location = /media/cdrom0
Link Target = /media/cdrom0/syslink.cfg.cpio

Could this be the culprit?

Thanks

---

### Post by mistypotato on 2007-01-11
bumpity...bumpity...........

---

### Post by mistypotato on 2007-01-11
When I do ls -la /media
Here's what I get....
I can't write to my DVD RW
Any ideas?
My DVD RWwill "read" ok as cdrom0
But I can write to it.


georgia@ubuntu:~$ ls -la /media
total 14
drwxr-xr-x  4 root    root    4096 2007-01-04 17:04 .
drwxr-xr-x 23 root    root    4096 2007-01-10 22:18 ..
drwxr-xr-x  2 root    root    4096 2007-01-04 17:04 cdrecorder
lrwxrwxrwx  1 root    root       6 2007-01-10 22:01 cdrom -> cdrom0
dr-xr-xr-x  2 georgia georgia 2048 2007-01-09 16:46 cdrom0
georgia@ubuntu:~$

---

