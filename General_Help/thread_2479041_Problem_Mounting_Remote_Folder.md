---
title: "Problem Mounting Remote Folder"
date: 2022-09-12
forum: General Help
---

### Post by waffen on 2022-09-12
Hello, 
In many Ubuntu PCs I have this code in the /etc/rc.local:

```

sleep 30
mount 192.168.1.250:/DOCUMENTOS/user/Juan /home/juan/G
exit 0

```

I just update from 20.04 to 22.04 and from  HD to SSD and that order never executes, but if I run it manually with sudo the folder is mounted with no issues, any idea why the folder is not mounted in auto when the OS startup?

Thanks!

---

### Post by TheFu on 2022-09-12
```
mount 192.168.1.250:/DOCUMENTOS/user/Juan /home/juan/G
```
shouldn't work.  the type of file system isn't specified.  Is there a reason you don't put this into the /etc/fstab?  That's what that file is for.  Just follow the template (see the comments or 'man fstab').

For nfs, It would look like this:

```
192.168.1.250:/DOCUMENTOS/user/Juan  /home/juan/G   nfs   nconnect=2,proto=tcp,rw,async  0 0
```

BTW, is it generally a bad idea to mount network storage under a user's HOME directory.  The best practice is to mount it elsewhere, then create a symlink from the HOME to the other location.

If it is CIFS, the options are different and the mount command posted shouldn't work, ever.  The format for a CIFS mount is different.

---

### Post by waffen on 2022-09-12
> **TheFu said:**
> ```
mount 192.168.1.250:/DOCUMENTOS/user/Juan /home/juan/G
```
shouldn't work.  the type of file system isn't specified.  Is there a reason you don't put this into the /etc/fstab?  That's what that file is for.  Just follow the template (see the comments or 'man fstab').

For nfs, It would look like this:

```
192.168.1.250:/DOCUMENTOS/user/Juan  /home/juan/G   nfs   nconnect=2,proto=tcp,rw,async  0 0
```



Works fine since Ubuntu 14, just with the upgrade to Ubuntu 22 the command is not loaded in the startup process.

Not a real reason, it's working till now, so I don't touch it.

Thanks for the idea, I'll check it tomorrow

---

### Post by TheFu on 2022-09-13
If it worked before, it was a bug.

---

### Post by waffen on 2022-09-14
> **TheFu said:**
> 
For nfs, It would look like this:

```
192.168.1.250:/DOCUMENTOS/user/Juan  /home/juan/G   nfs   nconnect=2,proto=tcp,rw,async  0 0
```


Hi, this works! thanks!

---

### Post by TheFu on 2022-09-14
> **waffen said:**
> Hi, this works! thanks!

I knew it would, if the storage was NFS.

You really shouldn't mount remote storage under any HOME directory as above.  Better to mount it somewhere like /media/G, and in your HOME, create a symbolic link from ~/G to /media/G/

Consider yourself warned.  Eventually, something terrible will happen if you leave it mounted the current way.  Please, please, learn from mistakes made by others. Please.

---

