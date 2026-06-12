---
title: "problems mounting gmailfs"
date: 2007-08-16
forum: General Help
---

### Post by writingsama on 2007-08-16
Hey. I know it's not supported, but maybe you can help anyway?

Here's what I  did:

I installed gmailfs. I can mount and use it...AS ROOT ONLY, which is a bit of a pain to say the least.


Steps taken:
1) Use synaptic to install
2) mkdir /media/gmailfs
3) mount -t gmailfs /usr/local/bin/gmailfs.py /media/gmailfs -o username=user,password=pass,fsname=random_fsname

if I do it without sudo, it gives an error:
mount: only root can do that

. if I sudo it, it works, but can only be accessed by root. I've chowned the directory /media/gmailfs both while mounted and not and no joy.

So, I tried adding it to fstab:

# /dev/gmailfs
/usr/local/bin/gmailfs.py /media/gmailfs gmailfs noauto,users,username=user,password=pass,fsname=random_fsname


When I attempt to mount:

mount /media/gmailfs
Ignored option :rw
Ignored option :noexec
Ignored option :nosuid
Ignored option :nodev
Ignored option :noauto
Ignored option :users
fuse: failed to exec fusermount: Permission denied
fuse: reading device: Bad file descriptor

but sudo'ing it appears to work:
sudo mount /media/gmailfs
Ignored option :rw
Ignored option :noexec
Ignored option :nosuid
Ignored option :nodev
Ignored option :noauto
Ignored option :users


...Any help? I just want to be able to mount as a user!
Thanks!

---

### Post by UK-Wobbie on 2007-08-16
> **writingsama said:**
> Hey. I know it's not supported, but maybe you can help anyway?

Here's what I  did:

I installed gmailfs. I can mount and use it...AS ROOT ONLY, which is a bit of a pain to say the least.


Steps taken:
1) Use synaptic to install
2) mkdir /media/gmailfs
3) mount -t gmailfs /usr/local/bin/gmailfs.py /media/gmailfs -o username=user,password=pass,fsname=random_fsname

if I do it without sudo, it gives an error:
mount: only root can do that

. if I sudo it, it works, but can only be accessed by root. I've chowned the directory /media/gmailfs both while mounted and not and no joy.

So, I tried adding it to fstab:

# /dev/gmailfs
/usr/local/bin/gmailfs.py /media/gmailfs gmailfs noauto,users,username=user,password=pass,fsname=random_fsname


When I attempt to mount:

mount /media/gmailfs
Ignored option :rw
Ignored option :noexec
Ignored option :nosuid
Ignored option :nodev
Ignored option :noauto
Ignored option :users
fuse: failed to exec fusermount: Permission denied
fuse: reading device: Bad file descriptor

but sudo'ing it appears to work:
sudo mount /media/gmailfs
Ignored option :rw
Ignored option :noexec
Ignored option :nosuid
Ignored option :nodev
Ignored option :noauto
Ignored option :users


...Any help? I just want to be able to mount as a user!
Thanks!
Have a go on going to (Administration -> Users and Groups) And in there go to
 (Manage Groups) You may see what you are looking for! If not have a go on Messagebus in the list.

If you do get.. Click on it and go to Properties and in that click on your user name and root!! :) I hope that will help you

P.s if that do not work make your own Group.. And put in it gmailfs then click on your user name and root!

---

### Post by anthony43 on 2008-02-15
Hi all !
Well, I did what writingsama did, and my user with who I'd like to not only mount gmailfs but also cd into it, is in the fuse groupe :
```
% groups anthony                                                                                          20:14 #6
anthony : anthony adm dialout cdrom floppy audio dip video plugdev scanner lpadmin admin fuse
```
but, here what he sees when gmailfs is mounted (by root) and types ls -al: 
```
?--------- ? ?       ?            ?                ? gmail
```
and he can't get into that directory ...
Is it possible for a non root user to use gmailfs ?
Thanks in advance for your answers !
Anthony

---

### Post by anthony43 on 2008-02-16
Hi evrybody !
I found the solution !
If you want to mount gmailfs without beeing root, you just have to type the following command :

```
# Mount
$ /sbin/mount.gmailfs /usr/bin/gmailfs.py ~/gmail/

# Umount
$ fusermount -u ~/gmail/
```

provided you copied /etc/gmailfs/gmailfs.conf to ~/.gmailfs

This page : 
[http://gentoo-wiki.com/HOWTO_GmailFS]("http://gentoo-wiki.com/HOWTO_GmailFS") helped me a lot !

---

