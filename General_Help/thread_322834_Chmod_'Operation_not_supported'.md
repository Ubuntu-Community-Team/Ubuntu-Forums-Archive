---
title: "Chmod 'Operation not supported'"
date: 2006-12-21
forum: General Help
---

### Post by bekok on 2006-12-21
Hey,

I tried to mount my Windows partitions with NTFS read and write possibility via this tutorial: [http://ubuntuguide.org/wiki/Ubuntu:Edgy#How_to_mount_Windows_partitions_.28NTFS.29_on_boot-up.2C_and_allow_users_read_and_write_access](http://ubuntuguide.org/wiki/Ubuntu:Edgy#How_to_mount_Windows_partitions_.28NTFS.29_on_boot-up.2C_and_allow_users_read_and_write_access)
It all worked fine, but i'm a slight problem atm.. Because I can access the folder (/media/Data) while being root in the console, but i can't access it as a normal user...
Now i wanted to change that via chmod and i tried this:
"sudo chmod a=rwx Data"
But when I do that I get this error:
"chmod: changing permissions of `Data': Operation not supported"

Does anyone know how to fix this... 'caus I really wanna access the partition without being root all the time :)

---

### Post by po0f on 2006-12-21
bekok,

NTFS filesystems don't support Linux permissions.  Have you tried adding "umask=000" to the options in /etc/fstab for that partition?
```
[FONT="Courier New"]/dev/hda1    /media/windows    ntfs-3g    defaults,umask=000,locale=en_US.utf8    0    0[/FONT]
```
(The above taken from the guide linked.)

---

### Post by bekok on 2006-12-21
Yeah it worked, danx a lot!

---

