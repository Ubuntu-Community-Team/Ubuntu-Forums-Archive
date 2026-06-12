---
title: "yea i just did something really dumb"
date: 2006-07-09
forum: General Help
---

### Post by cannibalbob on 2006-07-09
so the other day i accidentaly modified my user account to be only in the group 'plugdev' (meant to just add myself to the group).  now sudo doesn't work. is that because i'm no longer in the 'sudo' group?

what should happen now?  should i boot a rescue disk and modify /etc/group manually?

thanks for any help.

---

### Post by taurus on 2006-07-09
Yip.  You need to boot into recovery mode (from GRUB menu) and add yourself to groups adm & admin in /etc/group.  Reboot and everything should be fine again...
```

nano /etc/group

```

---

### Post by cannibalbob on 2006-07-09
thanks, i'll give it a shot momentarily.

---

### Post by cannibalbob on 2006-07-09
hmm... doesn't look like yaboot has a recovery mode like grub does.

---

### Post by taurus on 2006-07-09
> **cannibalbob said:**
> hmm... doesn't look like yaboot has a recovery mode like grub does.
Yaboot!!!  If there is no option to boot to recovery mode (single user mode), then boot with the Ubuntu desktop CD (LiveCD) and mount  your / partition.  Then edit your /etc/group...

---

