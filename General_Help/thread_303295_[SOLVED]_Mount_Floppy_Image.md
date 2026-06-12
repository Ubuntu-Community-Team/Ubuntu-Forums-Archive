---
title: "[SOLVED] Mount Floppy Image"
date: 2006-11-20
forum: General Help
---

### Post by CowzRule on 2006-11-20
Is it possible to mount a floppy image file (i.e. filename.ima) like you can mount an iso file?
Thanks

---

### Post by reid on 2006-11-20
Hey,
This is from the man page for mount:
```

THE LOOP DEVICE
       One further possible type is a mount via the loop device. For  example,
       the command

         mount /tmp/fdimage /mnt -t msdos -o loop=/dev/loop3,blocksize=1024

       will  set  up  the  loop  device  /dev/loop3  to correspond to the file
       /tmp/fdimage, and then mount this device on /mnt.

```

Hope that helps.

---

