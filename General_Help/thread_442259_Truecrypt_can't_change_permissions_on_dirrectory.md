---
title: "Truecrypt: can't change permissions on dirrectory"
date: 2007-05-13
forum: General Help
---

### Post by oldtappan on 2007-05-13
I mounted a USB drive that's entirely encrypted using TrueCrypt.  It's formatted in FAT32.  I created the TC volume and added files in Windows.  I mounted it on my Fiesty box and I can view and modify files on that volume w/o any problems.  So far so good.

Currently, the permissions are as follow for one of the directories.
[FONT="Courier New"]drwx------ 8 fred fred 65536 2007-04-22 16:58 Data[/FONT]

I execute " [FONT="Courier New"]sudo chmod 777 Data[/FONT]" yet the ls -l shows "[FONT="Courier New"]drwx------ 8 fred fred 65536 2007-04-22 16:58 Data[/FONT]"  The chmod had no effect.  

Why isn't this working?   Is it because the underlying filesystem is FAT32?

---

### Post by johannes on 2007-05-13
What command are you using to mount the volume?

---

### Post by oldtappan on 2007-05-13
> **johannes said:**
> What command are you using to mount the volume?

sudo truecrypt -u /dev/sdc1 /storage

---

### Post by johannes on 2007-05-13
I'm not entirely sure but I think the -u option might be the cause of this since it sets the ID (and probably permissions) of the filesystem to the user which started truecrypt (root I would guess).

Perhaps you should look at this guide to get permission to mount volumes as a normal user.
[http://gentoo-wiki.com/HOWTO_Truecrypt#Mount_volumes_as_a_normal_user](http://gentoo-wiki.com/HOWTO_Truecrypt#Mount_volumes_as_a_normal_user)

I don't think I can be of much more help since I only use FAT on a small outer "cover" volume and ext3 on the hidden "real" one. I never dare writing to the outer volume in fear of breaking the hidden one...

Although, if I remember correctly I mounted the volume with:
$ sudo truecrypt -M uid=$(id -u),gid=$(id -g) /dev/sda /media/disk
and then:
$ sudo chown -R user.group /media/disk
$ sudo chmod -R 666 /media/disk
and I could read/write to it with all users even if I mounted it as root.

---

### Post by oldtappan on 2007-05-13
Thanks for the pointers but for some reason, the chown and chmod commands don't seem to have an effect.  The perms for group and other simply won't have write enabled.  All my files/dirs look like this:
drwxr-xr-x 8 fred fred 65536 2007-05-12 10:03 Backups

Even this "sudo chmod -R 777 Backups" has no effect.

Any ideas?

---

### Post by oldtappan on 2007-05-22
I was able to resolve my problem.  The trick is to mount the TrueCrypt volume correctly by passing in the appropriate mount options:

sudo truecrypt --mount-options "rw,sync,utf8,uid=1000,umask=0000" /dev/sdb1 /storage


This [thread ]("http://forums.truecrypt.org/viewtopic.php?t=4803&highlight=permission")helped.

---

