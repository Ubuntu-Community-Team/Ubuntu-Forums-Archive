---
title: "Cannot mount volume, invalid mount option"
date: 2008-02-06
forum: General Help
---

### Post by Zurtex on 2008-02-06
Just installed Gusty and when I try and stick any USB flash drive I get the same error message:

"Cannot mount volume.

Invalid mount option when attempting to mount the volume 'RETIREDS'."

Where RETIREDS is the volume name in this case, but it happens for an USB pen drive I put in. Any help at all please?

---

### Post by Zurtex on 2008-02-06
Solved it by going to the terminal and typing:

sudo gedit /etc/fstab

And changing the line:

/dev/sdb1       /media/cdrom0   udf,iso9660 user,noauto,exec 0       0

too:

# /dev/sdb1       /media/cdrom0   udf,iso9660 user,noauto,exec 0       0

---

### Post by Atomjack Magazine on 2008-02-21
This worked for me.  Thanks.

You have any explanation (in noob terms, that is) for this problem?

---

### Post by ibbuntu on 2008-02-22
This worked for me too. Thanks!

> You have any explanation (in noob terms, that is) for this problem?

Well I have no CDROM drive, so I suspect in my case it was because /dev/sdb1 normally points to a CD drive, but in this case it was pointing to my USB drive, which isn't a CD drive hence the mount option error. Commenting out this line prevented Gutsy from trying to mount the USB stick as a CD drive and let it mount it properly.

---

### Post by dryhte on 2008-03-09
Thanks guys,

this solved it for me as well :)

---

### Post by xrecar on 2008-05-28
> **Zurtex said:**
> Solved it by going to the terminal and typing:

sudo gedit /etc/fstab

And changing the line:

/dev/sdb1       /media/cdrom0   udf,iso9660 user,noauto,exec 0       0

too:

# /dev/sdb1       /media/cdrom0   udf,iso9660 user,noauto,exec 0       0

Thak you soooo much it solved my problem!

---

### Post by mike16889 on 2008-06-27
Thanx man just installed eeeXubuntu on my eeepc and couldent get my sd card to work

---

