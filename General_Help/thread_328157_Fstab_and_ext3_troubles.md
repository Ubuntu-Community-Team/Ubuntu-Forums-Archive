---
title: "Fstab and ext3 troubles"
date: 2006-12-30
forum: General Help
---

### Post by vitious on 2006-12-30
Hi! I'm a new ubuntu user with some linux experience.
My trouble is:
I've got a normal user and a root user, as usual for me
Editing the fstab to give normal user rw permission on a second hard drive doens't seem to work
This is the line:

/dev/hda2    /confettino     ext3    defaults,user        0       0

my normal user still doens't have writing permission to write on the drive (neither on nautilus: right click ->create )

Would somebody tell me where I'm mistaking?
Thanks in advance!

---

### Post by taurus on 2006-12-30
Why don't you change it back to 

```
/dev/hda2   /confettino   ext3   defaults   0   1
```
in /etc/fstab but than change the permission for /confettino so your user can write to it...

```
sudo chmod -R 777 /confettino
```

p.s.  Probably have to reboot though!

---

### Post by vitious on 2006-12-30
Thanks! It worked!
Could you please tell me why it didn't work only with fstab? So that I learn for next time... Usually i never had to use chmod to change restrictions...
Thanks again!

---

