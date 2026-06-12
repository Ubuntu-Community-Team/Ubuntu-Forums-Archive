---
title: "Find processes using a disk/mount"
date: 2008-06-22
forum: General Help
---

### Post by josir on 2008-06-22
Hi folks, 

this is not a Ubuntu specific question but I think you can help.

I am trying to umount a secondary fat32 mount but I got the message that they are in use.

After some research, I found lsof command. As root, I issue:

lsof /dados
lsof /dev/hdb5

but both returns nothing. How can I discover which process is locking files on that device?

Thanks in advance,
Josir.

---

### Post by Vivaldi Gloria on 2008-06-22
Try

```
lsof +f -- /mountpoint
```

---

### Post by brian_p on 2008-06-22
> **josir said:**
> Hi folks, 

this is not a Ubuntu specific question but I think you can help.

I am trying to umount a secondary fat32 mount but I got the message that they are in use.

You cannot unmount a directory you in. cd somewhere else. If that's not the problem - pass.

---

### Post by josir on 2008-07-02
Sometimes I can umount and sometimes I dont.

I issue lsof and it returns nothing for the mount

I also issue: 

lsof | grep hdb5 (the device where partition is mounted)

and 

lsof | grep dados

I have all applications closed (except gnome services) and, as suggests brian_p, I am not "inside" directory.
Very strange indeed.

Does somebody has any other tip?

---

