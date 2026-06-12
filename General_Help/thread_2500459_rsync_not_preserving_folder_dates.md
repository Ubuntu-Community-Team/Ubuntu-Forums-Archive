---
title: "rsync not preserving folder dates"
date: 2024-09-02
forum: General Help
---

### Post by Kilarin on 2024-09-02
I'm using rsync to copy one drive to another using the command:
rsync -varzh fromdrive todrive

it does preserve the timestamp of copied files.  but the timestamp on all copied folders is NOT preserved, it is today's date/time.

Any idea what I am doing wrong?  Or is this just the way rsync works?

Thank you!

---

### Post by aljames2 on 2024-09-02
It may help if you show the full command that you use, between code tags.
Also, what is your filesystem at source, and target?

Also, in the manpage it says that -a is the same as -rlptgoD
With the options you show to use, -r is implied when you use -a.

---

### Post by Kilarin on 2024-09-02
Thank you for your reply!

command being used is:
```
rsync -varzh /media/donlad/expdrv/ ${bkpdrv}
```

And I see you are right.  -r is not necessary.
Any guess why folders do not preserve timestamp though?

---

### Post by aljames2 on 2024-09-02
My target matches source.

Run this on each and compare a directory that has a mix of folders & files. Mine are identical.

```
ls --full-time
```

If it is a local backup you don't need -z, compression is more for over SSH or some other remote protocol.

You may know this, but there are times when elevated permissions are used, in particular if the source you are backing up is root owned, such as things behind /etc /usr or similar. Also when remote locations are involved where you are trying to preserver users, groups, permissions, etc.

---

### Post by Kilarin on 2024-09-03
Thank you, it seems to be working now.  I'm not certain what I did wrong previously, but it was probably user error.

---

