---
title: "[SOLVED] Hard drive issues...."
date: 2007-09-24
forum: General Help
---

### Post by ShatoriKiriyama on 2007-09-24
wasn't getting any responses in the hardware forum so thought i'd post here...

my gf's families iMac G5 recently crapped out and they are sending it off for repair but they were warned that files on the HD would be lost and it would cost £69 to have them moved over so i offered to try and rescue the files myself.since its a HD from a G5 i'd guess it was formatted in a HFS format. is there any way to mount this in either Windows or Ubuntu?

i only need to be able to read from it since it would be just to rescue the files :)

the HD is a 160GB Western Digital Caviar and uses a SATA interface if that matters much.

---

### Post by McNils on 2007-09-24
yes.

mount -t hfs /dev/XXXX /mnt

You might need to install support for hfs first. (hfsplus and hfsutils)

---

### Post by ShatoriKiriyama on 2007-09-24
> **McNils said:**
> yes.

mount -t hfs /dev/XXXX /mnt

You might need to install support for hfs first. (hfsplus and hfsutils)

thanks a lot :D

i'll try that out as soon as i get back from college ^_^

---

