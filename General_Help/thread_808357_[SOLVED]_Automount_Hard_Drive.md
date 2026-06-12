---
title: "[SOLVED] Automount Hard Drive"
date: 2008-05-26
forum: General Help
---

### Post by Aeph on 2008-05-26
I have an nfts partition of media files. I would like to be able to mount this automatically when I start up Ubuntu so that I can use it without manually mounting it every single time I start my computer (despite the fact that this takes two seconds) or copy the files onto my Linux hard drive. In addition to this, I would like to not have the mounted volume to show up on the desktop. Are these possible?

---

### Post by ricky_bains on 2008-05-26
yes friend auto mounting is very much possible just open /etc/fstab with root privilege then add following lines to this file
/dev/**your hdd no.** /windows/C  ntfs ro,users,gid=users,umask=0002,nls=iso8859-1 0 0

---

### Post by Aeph on 2008-05-27
Here is the line I have entered into fstab:

/dev/sdb3	/media/disk	ntfs	ro,users,gid=users,umask=0002,nls=iso8859-1	0	0

When I try to mount it, I get the following error:

fuse: failed to access mountpoint /media/disk: no such file or directory

Shouldn't it create this directory when it is mounted?

---

### Post by forestpixie on 2008-05-27
> Shouldn't it create this directory when it is mounted?No - make the directory that you want it to mount in

```
sudo mkdir /media/disk
```

try 
```
sudo mount - a
```

If that's error free you should be home an dry

---

### Post by Aeph on 2008-05-27
That did it.

---

### Post by forestpixie on 2008-05-27
GReat - can you mark thread solved then please )

---

