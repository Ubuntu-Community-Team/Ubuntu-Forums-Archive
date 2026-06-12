---
title: "Messing around with /etc/fstab"
date: 2007-12-01
forum: General Help
---

### Post by NCLI on 2007-12-01
Okay, I really screwed up when editing my fstab fiule to mount an external NTFS HDD, and now I can't login to Ubuntu.- When I try, it says that the home fol,der is not availible, which is probably due to it being located on a seperate partition from the rest of the file system, which is not mounted anymore.

I did make a backup of the fstab file, but when I try to use the command "mv /etc/fstab.bak /etc/fstab" in recovery mode to restore it, I'm told that it doiesn't exist.

That's it, basically.

---

### Post by merlinus on 2007-12-01
Post your fstab.  It may be that in recovery mode, a different version of that file is being used.  If so, you can manually mount ubuntu and make the necessary changes.

Here is one way to do this:

```

sudo mkdir /media/ubuntu
sudo mount -t ext3 /dev/sda2 /media/ubuntu

```

(substitute your ubuntu partition for sda2)

---

### Post by NCLI on 2007-12-01
> **merlinus said:**
> Post your fstab.  It may be that in recovery mode, a different version of that file is being used.  If so, you can manually mount ubuntu and make the necessary changes.

Here is one way to do this:

```

sudo mkdir /media/ubuntu
sudo mount -t ext3 /dev/sda2 /media/ubuntu

```

(substitute your ubuntu partition for sda2)

What do I write to open /etc/fstab? I usually just use gedit, but it doesn't work in recovery mode.

Also, when I tried mounting like you wrote above, it said this after executing the second command:

"[    59.744000] VFS: Can't find ext3 filesystem on /dev/sda2.
mount: wrong fs type, bad option, bad superblock on /dev/sda2, missing codepage or helper program, or other error
In some cases useful info is found in syslog - trydmesg | tail or so"

---

### Post by merlinus on 2007-12-01
Your ubuntu install may not be on /dev/sda2, as my parenthetical comment indicated.

sudo fdisk -l will probably show you which one it is.

You may have to use nano or vi as a text editor in recovery mode.

---

### Post by NCLI on 2007-12-01
> **merlinus said:**
> Your ubuntu install may not be on /dev/sda2, as my parenthetical comment indicated.

sudo fdisk -l will probably show you which one it is.

You may have to use nano or vi as a text editor in recovery mode.

Sorry, didn't notice the comment at the end.

Anyway., I've got /etc/fstab open now, but how do I add the partition manually?

---

### Post by merlinus on 2007-12-01
Post details (e.g. partition, filesystem, mountpoint), as well as your current /etc/fstab.

Here is the relevant line from mine:

/dev/sda7 /home ext3  defaults 0 2

---

### Post by NCLI on 2007-12-01
> **merlinus said:**
> Post details (e.g. partition, filesystem, mountpoint), as well as your current /etc/fstab.

Here is the relevant line from mine:

/dev/sda7 /home ext3  defaults 0 2
If you need more than what I post below, just say so:

/dev/sda1: mountpoint: / , filesystem: ext3
/dev/sdd1: mountpoint: /media/500 , filesystem: ntfs
/dev/sdd1: mountpoint: /media/500 , filesystem: ntfs-3g
/dev/sda3/ mountpoint: swap , filesystem: ?

---

### Post by merlinus on 2007-12-01
So try adding

/dev/sda4 /home ext3 defaults 0 2

to /etc/fstab

and restart.

You do not have to use uuids.

---

### Post by NCLI on 2007-12-01
> **merlinus said:**
> So try adding

/dev/sda4 /home ext3 defaults 0 2

to /etc/fstab

and restart.

You do not have to use uuids.

Wll that really messed things up, now I can't even access the login screen anymore :S

Also, when I try to edit /ets/fstab again from recovery mode, I get the message "The command could not be located because '/usr/bin' is not included in the PATH environment variable."

I also get an error mesage about the file system check failing when booting into recovery mode.

---

### Post by merlinus on 2007-12-01
You might try booting from a live linux cd, mounting ubuntu, and then editing /etc/fstab.

---

### Post by NCLI on 2007-12-01
Guess so, but it's bothersome. Thanks for trying anyway.

---

