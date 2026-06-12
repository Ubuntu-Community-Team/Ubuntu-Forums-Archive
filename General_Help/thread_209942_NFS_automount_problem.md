---
title: "NFS automount problem"
date: 2006-07-05
forum: General Help
---

### Post by Kilz on 2006-07-05
I have a file server/Direct connect hub that i recently changed over to Ubuntu. Windows is gone from my network :D  So I thought I would get rid of samba since it freezes during file transfer sometimes. I setup NFS, on the server , setup the shares. I made the mount points on my main desktop. I can mount the share in the terminal with mount. But I cant get it to auto mount with fstab. Here is the line from my fstab

//192.168.0.108:/files /mnt/files nfs rw,hard,usr,auto 0 0

Here is what mounts it in the terminal

sudo mount 192.168.0.108:/files /mnt/files

Can anyone point out what Im doing wrong? I have tried removing the // but still no auto mount.

---

### Post by scxtt on 2006-07-05
try:
[indent]//192.168.0.108:/files /mnt/files nfs rw,hard,[color=red]user[/color],auto 0 0[/indent]instead ...

---

### Post by Kilz on 2006-07-06
[QUOTE=scxtt]try:
[indent]//192.168.0.108:/files /mnt/files nfs rw,hard,[color=red]user[/color],auto 0 0[/indent]instead ...[/QUOTE]
Thanks for the reply, I fixed that, and it still will not automount.

---

### Post by echo $USER on 2006-07-06
This is the correct syntax

> //192.168.0.108:/files     -t nfs      /mnt/files     defaults      0       0

---

### Post by Kilz on 2006-07-06
[QUOTE=echo $USER]This is the correct syntax[/QUOTE]
Thanks, it wast the answer, but it was part of the answer. 

192.168.0.108:/files /mnt/files nfs defaults 0 0 

The above line in fstab automaticly mounts the folder in mount at startup
Thanks echo $USER and scxtt for helping me figure this out.

---

### Post by echo $USER on 2006-07-06
Oh yeah, sorry about that. If you want to mount it manually, you have to specify the the filesystme with the -t command like 

 > mount -t nfs 192.168.x.x:/shared/folder /mount/point

---

