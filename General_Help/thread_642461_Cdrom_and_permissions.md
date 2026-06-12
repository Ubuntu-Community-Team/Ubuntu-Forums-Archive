---
title: "Cdrom and permissions"
date: 2007-12-16
forum: General Help
---

### Post by alucardx on 2007-12-16
I just installed Ubuntu.  I can't get the system to let my user, which has cdrom permissions, which is allowed in fstab to have permissions, to let me  copy or read files from a cdrom.  I double click on an image that is store on the cd and it tells me that I don't have the permissions to do that.  I try copying it in nautilus or bash and the same thing happens.  Where in the system is the permission that is stopping me from doing this?  I normally use Slackware and everything there is very straight-forward.  Maybe I'm missing something very obvious though.

---

### Post by DoctorMO on 2007-12-16
use `ls -l /media` to tell you what the current permissions are.

Have you at all messaged about witht he fstab entry?

---

### Post by alucardx on 2007-12-16
lrwxrwxrwx 1 root root    6 2007-12-12 16:08 cdrom -> cdrom0
drwxr-xr-x 2 root root 4096 2007-12-12 16:08 cdrom0
lrwxrwxrwx 1 root root    7 2007-12-12 16:08 floppy -> floppy0
drwxr-xr-x 2 root root 4096 2007-12-12 16:08 floppy0


Those are the permissions for the content of my media folder.

---

### Post by scizzo on 2007-12-16
Can you please post what the command for the user:

# groups

And also what is in the fstab for the cdrom?

Also can you access the cdrom without problems when using sudo?

---

### Post by alucardx on 2007-12-16
groups alucardx
alucardx : alucardx adm dialout cdrom floppy audio dip video plugdev scanner lpadmin admin netdev powerdev

/dev/scd0       /media/cdrom0   auto ro,users,noauto,exec 0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec 0       0


I can do anything I want with the cdrom as root.  Shall I still try using sudo?

---

### Post by scizzo on 2007-12-16
why is fstab for cdrom saying 'users' and not 'user'?

Not sure if that is a valid mount option.

---

### Post by alucardx on 2007-12-16
I tried both ways.  Here is the excerpt from the man page for "mount".

              user   Allow an ordinary user to mount  the  file  system.   The
                     name  of  the mounting user is written to mtab so that he
                     can unmount the file system again.  This  option  implies
                     the  options noexec, nosuid, and nodev (unless overridden
                     by  subsequent   options,   as   in   the   option   line
                     user,exec,dev,suid).

              users  Allow  every  user  to mount and unmount the file system.
                     This option implies the options noexec, nosuid, and nodev
                     (unless  overridden  by  subsequent  options,  as  in the
                     option line users,exec,dev,suid).


I could be misinterpreting it though.  Anything else we should look at?

---

### Post by Rumo on 2007-12-17
I had the same problem. It somehow disappeared overnight (not sure if this was because of an update).

In my case /dev/scd0 had the wrong permissions (or the wrong group; 'root' instead of 'cdrom'):
```

brw-rw---- 1 root root 11, 0 2007-12-17 20:19 /dev/scd0

```
A temporary fix is to change the group with the following command: 'sudo chgrp cdrom /dev/scd0'. You will have to do this on every reboot, though (unless your problems mysteriously disappear like mine). I'm not really sure which config files are responsible for this (/etc/fstab is certainly one of them).

---

### Post by alucardx on 2007-12-17
The interesting thing about this though is that the group was cdrom.  I even gave read and execute access to everyone and it still wouldn't work unless I was root.  My only thought is that there is something fubar in the automount process.  Or just some insanely strange glitch.

...wish I knew.

Thanks to everyone so far for the replies though.

---

