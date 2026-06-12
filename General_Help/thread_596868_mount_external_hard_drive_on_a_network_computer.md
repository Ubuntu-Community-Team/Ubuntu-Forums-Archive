---
title: "mount external hard drive on a network computer"
date: 2007-10-30
forum: General Help
---

### Post by greenlegacy on 2007-10-30
I'm trying to mount an external hard which is connected to a different computer on my network.  

I can see that the drive is mounted and I can access the files when I ssh into the server, and my nfs share seems to be working, but it doesn't show any files in directory the external hard drive is mounted to when I'm trying to access them from a different computer.

---

### Post by dayvy on 2007-10-30
If I understand correctly, you are trying to mount this remote external drive via nfs. If you can access the files via ssh then I would suggest that there is a problem with your nfs configuration. If you give us more details we'll try to help.

d.

---

### Post by greenlegacy on 2007-11-01
Yes, that's what I'm trying to do.  I'll try to be more specific.  I'm just not sure why I can't see any of the folders in it from a different computer on the network.

Here is what is in my /etc/exports on the remote computer.
```

/home/greenlegacy/mnt 192.168.1.100(rw)

```

I used this command to mount the external drive to the remote computer in the first place:
```

sudo mount -t vfat -o gid=greenlegacy,uid=greenlegacy /dev/sdb1 /home/greenlegacy/mnt

```

Then I mount the directory with:
```

sudo mount 192.168.1.102:/home/greenlegacy/mnt /media/external_drive

```

This results in a permission denied error:
```

mount.nfs: 192.168.1.102:/home/greenlegacy/mnt failed, reason given by server: Permission denied

```

---

