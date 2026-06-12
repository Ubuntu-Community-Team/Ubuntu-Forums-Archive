---
title: "sbackup after a total fresh reinstall"
date: 2007-08-29
forum: General Help
---

### Post by sdowney717 on 2007-08-29
If I do an sbackup, save the directory of backed up stuff.
And then take this to another system or do a fresh install of ubuntu,
can I do a restore and expect to see menu items back like they were?
What exactly is 'restored' just copying home files or is it doing something greater.
like setting up the system to be just as it was before.

---

### Post by TheExplorer on 2007-08-29
As I remember you can specify ANY folder of your system to be backed up. Actually, I faced some problems with sbackup in the past. Not everything I backed up could be restored properly as I wanted so I don't use it anymore. You better just copy the most vital part of the system to another partition or burn CD. After the fresh reinstall simply copy the files back. Copy the following folders to get your settings and programs back:
> /bin
/boot
/etc
/home
/lib
/root
/sbin
/usr


---

### Post by ruibernardo on 2007-08-29
If you backup your /home folder and **create the same users by the same order** in the new install, you shouldn't have any problem.

Sbackup can do this. [HUBackup]("https://wiki.ubuntu.com/HomeUserBackup") can do it too.

Sbackup wasn't made for complete backups and total restores, although it can be done if:

- you backup all the folders in / (some can't be backed up like /proc /dev /sys. Other you don't want to, like /media);
- reinstall them in the new disc/partition(s);
- run grub-install on the new disc/partition;
- recreate the folders that couldn't be backup (/proc /mnt /media/ /sys);
- update the UUID's in /etc/fstab and /boot/grub/menu.lst.

This might be incomplete. It's really *reeeally* a very hard work to be done with sbackup.

---

