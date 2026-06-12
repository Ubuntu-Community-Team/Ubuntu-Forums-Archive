---
title: "Hard Drives unmounting on restart"
date: 2007-01-28
forum: General Help
---

### Post by Goodfox on 2007-01-28
I had to reinstall Ubuntu the other day to sort out a few speed problems, which it seemed to fix straight away.
But the one problem I've had since reinstalling is getting my hard drives to stay mounted, although they worked perfectly before the reinstallation.

I've added this to the end of my fstab file:

/dev/hda1	/media/Windows 	ntfs ro,users,noauto,uid=1000,gid=1000 0 0
/dev/hda5	/media/Other 	ntfs ro,users,noauto,uid=1000,gid=1000 0 0

And I've mounted the hard drives with:

mount /media/Windows
mount /media/Other

But on restart, both disappear and I have to remount them both. I'm sure I did it exactly the same way before and it worked, but they won't stay mounted at all now after I restart.
If it helps, I'm using Ubuntu 6.10.

Thanks in advance for any help or advice.

---

### Post by Ramses de Norre on 2007-01-28
Replace "noauto" by "auto" ;)

---

### Post by Goodfox on 2007-01-28
That did the trick =)

Thanks.

---

