---
title: "Cannot select drive D:"
date: 2007-08-08
forum: General Help
---

### Post by akb on 2007-08-08
Hi there,

I am trying to install Wubi/Ubuntu onto my second hdd, but I cannot select it - the dropdown field shows me only drive C:

Do you have an idea how to solve this?

My config is like

C: == Nforce4 RAID (RAID0/Stripe) of two SATA disks
D: == DVD-Writer
Q: == Single SATA disk

Q: is the drive of my choice, but it isn't shown in the dropdown... :-/

---

### Post by ago on 2007-08-08
That's because there is not enough free space. You need 5GB+

---

### Post by akb on 2007-08-08
But it has about 25 gigs free.

---

### Post by ago on 2007-08-08
Then for some reason it's not reading the size correctly or it does not see the drive at all. You'd need to run the nsis code directly to know for sure. Anyway you can install on c: and then move the folder on d:. That will put off the uninstaller but otherwise it will work.

---

### Post by akb on 2007-08-08
Hmmm... okay. And where do I have to change path entries?

---

### Post by ago on 2007-08-08
Running nsis from source is probably too complicated if you are not a developer, you are better off simply installing on C: and then moving on Q:

It might also be that the letter Q: is too "high", I'll need to check, but you can try to change the drive letter to E: F: or similar

---

