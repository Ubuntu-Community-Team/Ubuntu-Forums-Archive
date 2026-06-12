---
title: "LVM Create with nbd error"
date: 2007-05-28
forum: General Help
---

### Post by adrenaline_nz on 2007-05-28
Hi all,

I have created a RAID 5 array from 3 500GB drives which has gone well from what I can tell so far, I am now in the process of attempting to create an LVM group to place the RAID 5 array in.

I have downloaded and installed LVM2, I have then tried to run

```
sudo vgcreate media /dev/md0
```

After that is entered I get the following, which is followed with the message that the volume group was successfully created:

```
nathan@dcerouter:~$ sudo vgcreate media /dev/md0
  /dev/nbd0: read failed after 0 of 4096 at 0: Input/output error
  /dev/nbd1: read failed after 0 of 4096 at 0: Input/output error
  /dev/nbd2: read failed after 0 of 4096 at 0: Input/output error
  /dev/nbd3: read failed after 0 of 4096 at 0: Input/output error
  /dev/nbd4: read failed after 0 of 4096 at 0: Input/output error
  /dev/nbd5: read failed after 0 of 4096 at 0: Input/output error
  /dev/nbd6: read failed after 0 of 4096 at 0: Input/output error
  /dev/nbd7: read failed after 0 of 4096 at 0: Input/output error
  /dev/nbd8: read failed after 0 of 4096 at 0: Input/output error
  /dev/nbd9: read failed after 0 of 4096 at 0: Input/output error
  /dev/nbd10: read failed after 0 of 4096 at 0: Input/output error
  /dev/nbd11: read failed after 0 of 4096 at 0: Input/output error
  /dev/nbd12: read failed after 0 of 4096 at 0: Input/output error
  /dev/nbd13: read failed after 0 of 4096 at 0: Input/output error
  /dev/nbd14: read failed after 0 of 4096 at 0: Input/output error
  /dev/nbd15: read failed after 0 of 4096 at 0: Input/output error
  /dev/nbd0: read failed after 0 of 4096 at 0: Input/output error
  /dev/nbd0: read failed after 0 of 4096 at 2199022141440: Input/output error
  /dev/nbd0: read failed after 0 of 4096 at 0: Input/output error
  /dev/nbd1: read failed after 0 of 4096 at 2199022141440: Input/output error
  /dev/nbd1: read failed after 0 of 4096 at 0: Input/output error
  /dev/nbd2: read failed after 0 of 4096 at 2199022141440: Input/output error
  /dev/nbd2: read failed after 0 of 4096 at 0: Input/output error
  /dev/nbd3: read failed after 0 of 4096 at 2199022141440: Input/output error
  /dev/nbd3: read failed after 0 of 4096 at 0: Input/output error
  /dev/nbd4: read failed after 0 of 4096 at 2199022141440: Input/output error
  /dev/nbd4: read failed after 0 of 4096 at 0: Input/output error
  /dev/nbd5: read failed after 0 of 4096 at 2199022141440: Input/output error
  /dev/nbd5: read failed after 0 of 4096 at 0: Input/output error
  /dev/nbd6: read failed after 0 of 4096 at 2199022141440: Input/output error
  /dev/nbd6: read failed after 0 of 4096 at 0: Input/output error
  /dev/nbd7: read failed after 0 of 4096 at 2199022141440: Input/output error
  /dev/nbd7: read failed after 0 of 4096 at 0: Input/output error
  /dev/nbd8: read failed after 0 of 4096 at 2199022141440: Input/output error
  /dev/nbd8: read failed after 0 of 4096 at 0: Input/output error
  /dev/nbd9: read failed after 0 of 4096 at 2199022141440: Input/output error
  /dev/nbd9: read failed after 0 of 4096 at 0: Input/output error
  /dev/nbd10: read failed after 0 of 4096 at 2199022141440: Input/output error
  /dev/nbd10: read failed after 0 of 4096 at 0: Input/output error
  /dev/nbd11: read failed after 0 of 4096 at 2199022141440: Input/output error
  /dev/nbd11: read failed after 0 of 4096 at 0: Input/output error
  /dev/nbd12: read failed after 0 of 4096 at 2199022141440: Input/output error
  /dev/nbd12: read failed after 0 of 4096 at 0: Input/output error
  /dev/nbd13: read failed after 0 of 4096 at 2199022141440: Input/output error
  /dev/nbd13: read failed after 0 of 4096 at 0: Input/output error
  /dev/nbd14: read failed after 0 of 4096 at 2199022141440: Input/output error
  /dev/nbd14: read failed after 0 of 4096 at 0: Input/output error
  /dev/nbd15: read failed after 0 of 4096 at 2199022141440: Input/output error
  /dev/nbd15: read failed after 0 of 4096 at 0: Input/output error
  Volume group "media" successfully created
```

Does anyone have any idea what has happened or if I should worry about it?

Thanks

---

### Post by fanatik on 2007-05-29
these are network block devices - are you using these in any way? you can safely ignore these messages if you aren't, in fact you can and probably should configure lvm to ignore them too, it will be quicker that way as well. have a look at /etc/lvm/lvm.conf and look for the filter line, you can accept and reject only the devices you want  to use there. 

hope that helps

---

### Post by adrenaline_nz on 2007-05-29
> **fanatik said:**
> these are network block devices - are you using these in any way? you can safely ignore these messages if you aren't, in fact you can and probably should configure lvm to ignore them too, it will be quicker that way as well. have a look at /etc/lvm/lvm.conf and look for the filter line, you can accept and reject only the devices you want  to use there. 

hope that helps

Thanks worked a treat :)

---

### Post by cokegen on 2007-12-07
One can avoid those messages, as everyone has said here, implementing a filter like this in /etc/lvm/lvm.conf

filter = [ "r|/dev/cdrom|", "r|/dev/nbd|" ]

This was just to give an example that works.

Cheers,


Carlos

---

