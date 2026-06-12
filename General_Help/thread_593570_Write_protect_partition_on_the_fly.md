---
title: "Write protect partition on the fly?"
date: 2007-10-27
forum: General Help
---

### Post by QwUo173Hy on 2007-10-27
I have a partition I want to be able to make read only from time to time (when the kids are using the machine). Can I do this on the fly? Currently, I'm editing fstab constantly and it's driving me crazy!

Thanks,
Jarlath

---

### Post by nick_h on 2007-10-27
Yes, you can use the umount and mount commands.  For example:
```
sudo umount /dev/sda2
sudo mount -o ro /dev/sda2 /media/sda2
```
This will unmount a partition and remount it as read-only.  You probably will need to add other options along with ro (those in your fstab).

You could put these commands in a script to make things easier.

Another way would be to create a different account for your kids to use and make the partition read-only for that account.

---

### Post by kellemes on 2007-10-27
> **jarlath said:**
> I have a partition I want to be able to make read only from time to time (when the kids are using the machine). Can I do this on the fly? Currently, I'm editing fstab constantly and it's driving me crazy!

Thanks,
Jarlath

Why not create a new user.. like "kids" and give them the needed permissions? You can use mount options in fstab to set what user/group can write or read a device.
You can simply switch user on the fly.
This is just the thing where GNU/Linux is King.

---

### Post by nick_h on 2007-10-27
> **kellemes said:**
> Why not create a new user.. like "kids" and give them the needed permissions?
I think the new user approach is the better solution.

---

### Post by QwUo173Hy on 2007-10-29
Thanks guys. I like the sound of the new user. I didn't realize I could do that though. Thanks kellemes, I'll look into it. Gnome doesn't give you this option when you create a new user so I'll try the RUTE manual.

Jarlath

---

