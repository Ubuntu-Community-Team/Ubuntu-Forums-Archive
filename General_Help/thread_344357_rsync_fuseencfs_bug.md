---
title: "rsync fuse/encfs bug"
date: 2007-01-22
forum: General Help
---

### Post by theOrange on 2007-01-22
Ok - so i am using edgy. I use fuse to mount a encfs on an usb hard drive and use rsync to back up my home directory. Used to work very well until...

[https://bugzilla.samba.org/show_bug.cgi?id=3752](https://bugzilla.samba.org/show_bug.cgi?id=3752)

Thus now rsync doesn't work properly b/c of the timestamp being reset rsync always recopies the files! 

The bug was closed out on rsync but i couldn't follow the solution. Is this something that can be fixed with newer encfs/fuse? The latest encfs is 1.3.1 while edgy has 1.2.5 and I see edgy only has fuse 2.5.3 while the latest release is fuse 2.6.1. 

Is this planned for feisty? 

How do i get this backported?

I am not sure where to go from here so any direction would be much appreciated! This really makes a secure backup using rsync/encfs a PITA.

Thanks

---

