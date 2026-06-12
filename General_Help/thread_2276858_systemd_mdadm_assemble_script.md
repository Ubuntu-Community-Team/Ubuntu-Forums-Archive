---
title: "systemd mdadm assemble script"
date: 2015-05-05
forum: General Help
---

### Post by xWEkxhW on 2015-05-05
Hello,

Can anyone assist me with writing a systemd script to assemble my imsm raid5 volume during boot, so that it's done before networking?

Effectively I'd like to run the command:

mdadm --assemble --scan

During the boot, once the local filesystems have been mounted but before networking is up.

Thanks

---

### Post by dino99 on 2015-05-05
that thread about mounting raid5 too  [http://superuser.com/questions/850738/systemd-cant-mount-partition](http://superuser.com/questions/850738/systemd-cant-mount-partition)

---

### Post by xWEkxhW on 2015-05-05
> **dino99 said:**
> that thread about mounting raid5 too  [http://superuser.com/questions/850738/systemd-cant-mount-partition](http://superuser.com/questions/850738/systemd-cant-mount-partition)

Thanks, I'll take a look

---

