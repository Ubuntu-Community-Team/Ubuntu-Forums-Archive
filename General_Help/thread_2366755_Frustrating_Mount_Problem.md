---
title: "Frustrating Mount Problem"
date: 2017-07-21
forum: General Help
---

### Post by cathect2 on 2017-07-21
[Using 16.04]

I have a NAS with a cifs share that I automount on my desktop. However, the mounting behaves strangely and I need some help. Here's the issue:

1. When I boot my machine, I run a backup script that backs up my /home folder to the NAS share.
2. The share appears in my dash as a mounted folder (but as you will see below, it is sort of a "soft" mount).
3. The script fails with a "Permission denied (13)" error.

**HOWEVER:**

4. If I click into the folder, I hear the disk spin up in my FreeNas, and the folder becomes browsable.
5. The script will then run as expected. 

I suspected that Ubuntu was trying to mount the drive before networking was established during boot, so I added _netdev to my fstab entry. It looks like this:

```
//192.168.1.77/Media /media/NAS-Media cifs users,noauto,_netdev,credentials=/home/cathect/.smbcredentials 0 0
```

But this doesn't work either. 

I'd like ubuntu to mount this drive so that, after login, my script will run and perform the backup without intervention. But I am unable to mount this drive completely until I actively browse it with nautilus. Help!

---

### Post by TheFu on 2017-07-21
If you are using freenas, why not use the native file sharing for Unix systems, NFS?  This would provide a server-to-server connection, not tied to any specific userid.  The underlying file systems on freenas should be ZFS which completely supports NFS.

---

### Post by Morbius1 on 2017-07-21
> //192.168.1.77/Media /media/NAS-Media cifs users,[COLOR=#0000cd]**noauto**[/COLOR],_netdev,credentials=/home/cathect/.smbcredentials 0 0
By specifying [COLOR=#0000cd]**noauto**[/COLOR] you have told Linux not to mount this share on boot.

Side note:
> The share appears in my dash as a mounted folder (but as you will see below, it is sort of a "soft" mount).
I don't think it's showing up as mounted folder. It's showing up as a "mountable" folder since the mount point is under /media. That's a udisks thing.

---

### Post by cathect2 on 2017-07-21
As I understand it, noauto option won't make a difference since the network isn't yet available during boot. I've tried it without . . . no joy. 

But I did find a solution! You have to use **x-systemd.automount** as an option in fstab. Works.

---

