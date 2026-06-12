---
title: "Adding a hard disk to Edgy"
date: 2006-11-22
forum: General Help
---

### Post by hornett on 2006-11-22
Hello, I'm running Edgy on a machine which needs a shared XP/Linux storage disk.

I've formatted it FAT32, it works in Windows, and can be mounted in Edgy with no problems, but how do I install it permanently in Ubuntu?

GParted, the partition manager used to have options to set mount points and stuff like that, but now they are gone. 

I am not feeling confident about editing the fstab either, since the devices are not listed anymore like "/dev/hda" but now they are listed as a big code like "Ue2087423098432098503498509348503498509348". What's the advantage to that then?! :-D 

PS. on Dapper, when you mounted a drive in /media, it would appear by itself on the desktop. Is this supposed to happen on Edgy?

Thanks all,
Andy.

---

### Post by JShadow on 2006-11-22
I think the mounting part got removed due to no one maintaining it.

The best way would be to add the drive to fstab. Add a line similar to this:

/dev/hdb1 /media/seconddrive vfat defaults 0 0

You don't need to use code that Ubuntu has in there.

---

### Post by taurus on 2006-11-22
> **JShadow said:**
> I think the mounting part got removed due to no one maintaining it.

The best way would be to add the drive to fstab. Add a line similar to this:

/dev/hdb1 /media/seconddrive vfat defaults 0 0

You don't need to use code that Ubuntu has in there.
Modify that one above a little to make it look more like this!

```
/dev/hdb1 /media/seconddrive vfat defaults,umask=000 0 0
```

---

### Post by hornett on 2006-11-22
> **taurus said:**
> Modify that one above a little to make it look more like this!

```
/dev/hdb1 /media/seconddrive vfat defaults,umask=000 0 0
```

Thanks! Mine was already exactly like this, as it was for me in Dapper. I still don't get a drive on the desktop showing up. :confused:

---

### Post by taurus on 2006-11-22
Okay, what are the output of these commands from a terminal?

```
cat /etc/fstab
df -h
```

---

### Post by hornett on 2006-11-22
Problem solved, unfortunately not sure what fixed it since I changed several things since last reboot ](*,) ](*,) ](*,) 

Anyway it's fixed now so it's all good. :cool: 

Does anybody know what is benefit of using the weird U345345345... codes to reference the drives in the fstab and menu.lst files ?

---

