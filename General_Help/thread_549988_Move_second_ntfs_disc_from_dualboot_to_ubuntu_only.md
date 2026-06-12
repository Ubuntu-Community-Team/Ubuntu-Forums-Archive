---
title: "Move second ntfs disc from dualboot to ubuntu only computer?"
date: 2007-09-13
forum: General Help
---

### Post by plo on 2007-09-13
Hi!

I want to move a second internal disc (with music and movies) from my dualboot (Win+Ubuntu) to my new htpc (Ubuntu). The drive is current NTFS and I use ntfs-config to access it when I boot Ubuntu.

Any tips:

* Do I need to unmount it in Ubuntu, before I shutdown? Or can I just remove it and install it in the new computer? If I need to unmount, how do I do that in Ubuntu?
* After I move it I still want to be able to access the disc from a windows computer (over LAN).
 Is it still better to reformat it to ext3 or should I keep it as NTFS? Do I then need samba to allow windows to access that disc?
* If I change to ext3 do I need to erase format the disc or can I change it "on the fly" - (yes I will create backup first)? And do I do that before or after I move the disc?
I have a Parted Magic boot disc avilable.

Appreciate any support. 
/Pålle

---

### Post by prince_niceguy on 2007-09-13
I would have done it the following way.

Assuming PC A is current PC with ubuntu and windows and PC B is only ubuntu.

1. You can safely remove the disk after shutdown from A and move to B.
2. Yes you can access B from A. You can use samba for sharing the drive in A and then access it from B either from windows or ubuntu. 
3. For converting to ext3 you will have to reformat the drive. There is no other option to convert on the fly.

---

### Post by plo on 2007-09-13
Thanks!

Which is better keep NTFS or change to ext3?

/Pålle

---

### Post by prince_niceguy on 2007-09-13
depends what would be your primary access OS. linux or windows...

if linux then use ext3 or better still use reiserfs or xfs

if windows then use ntfs

---

