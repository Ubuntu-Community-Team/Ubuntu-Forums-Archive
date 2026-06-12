---
title: "cannot unmount remote samba folder"
date: 2007-02-06
forum: General Help
---

### Post by xpan on 2007-02-06
hi,

I have this line on my fstab


//192.168.1.15/public2  /mnt/pub        smbfs   defaults 0 0

when I type # mount /mnt/pub

it works fine, but when I try to umount /mnt/pub (as root again) I get this:

umount: /mnt/pub: device is busy
umount: /mnt/pub: device is busy

(yes, twice)

why?

---

### Post by xpan on 2007-02-06
please delete this thread! I am stupid. 
I was trying to umount while being inside the mount-ed folder...

---

### Post by 1longtime on 2008-03-23
NOOO do NOT delete this thread, I just did the same thing and this thread set me straight in 60 seconds!  I <3 Google.

---

### Post by Oldsoldier2003 on 2008-03-23
> **1longtime said:**
> NOOO do NOT delete this thread, I just did the same thing and this thread set me straight in 60 seconds!  I <3 Google.

Threads don't get deleted in The Ubuntu Forums for just that reason :)

---

