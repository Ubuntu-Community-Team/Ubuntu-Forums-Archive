---
title: "Problems with writing files"
date: 2019-05-07
forum: General Help
---

### Post by jangel98 on 2019-05-07
Hola, necesito ayuda general. Tengo instalado en mi laptop Windows 10 y Kubuntu 18.04, el caso es que muchas veces cuando inicio en Kubuntu no me permite modificar los archivos de la particion en la que tengo los datos personales. Este tiene sistema de archivo ntfs, y la particion de kubuntu esta en ext4. Si alguien tiene alguna idea, por favor ayudenme.

Hi, i need general help. I have dual-boot in mi laptop, Windows 10 and Kubuntu 18.04, the problem is, many times, when I boot with Kubuntu, it's unable to write into the data partition(NTFS). Kubuntu partition is Ext4. If anyone has any ideas, please help me.

---

### Post by wildmanne39 on 2019-05-07
You have posted in an English only sub-forum, so please post in English in the future, if you want to post in your native language please locate the appropriate sub-forum.

Thanks!

---

### Post by TheFu on 2019-05-07
For NTFS storage, permissions are controlled by mount options.  These forums have many example mount commands for NTFS or you can use the fstab file, which will also need those permissions.
[https://help.ubuntu.com/community/MountingWindowsPartitions](https://help.ubuntu.com/community/MountingWindowsPartitions)

After the NTFS is mounted, there is nothing that can be done. chown and chmod do not work.

Under Windows, I've heard there are special drivers to access ext2/3 partitions, but have never used those.

This issue comes up all the time, so there should be solutions posted all over the internet in pretty much every language.

This is how I do it - the variables need to either be set or replaced by what makes sense for your system. The mount location, i.e. directory, needs to exist.
```
$ sudo mount -t ntfs -o uid=$UID,gid=$GID LABEL=$LABEL8 /mnt/$LABEL8
```

---

