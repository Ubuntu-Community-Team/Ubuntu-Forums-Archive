---
title: "cdrom"
date: 2016-04-09
forum: General Help
---

### Post by ErwinK on 2016-04-09
Ihave been using ubuntu for some time but yesterday when I started ubuntu it comes up with the following message, An error occurred while mounting/mnt/cdrom
Press S to skip mounting of M for manual recovery.
What do I do?

ErwinK

---

### Post by howefield on 2016-04-10
Is the cdrom being mounted with fstab ?

What is the output of ...

```
cat /etc/fstab
```

---

### Post by ErwinK on 2016-04-10
Here is the result of the fstab.
# /etc/fstab: static file system information.
#
# Use 'blkid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
# / was on /dev/sdb1 during installation
UUID=d4b4e2d9-6964-4471-88a2-40610754900f /               ext4    errors=remount-ro 0       1
# swap was on /dev/sdb6 during installation
UUID=81e06e18-02a2-4450-8eb4-c8126537b7f1 none            swap    sw              0       0
/dev/cdrom /mnt/cdrom auto nosuid,nodev,nofail,x-gvfs-show 0 0
erwin@erwin-HP-Pavilion-dv7-Notebook-PC:~$ 
I am not sure about to much of what goes on. I mainly just use the program.

---

### Post by howefield on 2016-04-10
Are you comfortable with the terminal ?

If so..

```
sudo cp /etc/fstab /etc/fstab.old
```

which will create a copy of your fstab file in case you mess up. Then..

```
sudo nano /etc/fstab
```

and put a hash sign (#) in front of the cdrom line so it looks like..
```
# /dev/cdrom /mnt/cdrom auto nosuid,nodev,nofail,x-gvfs-show 0 0
```

Then Ctrl + o keys to save the file, press enter and then Ctrl + x keys to exit.

You can do this graphically if that suits you better with

```
sudo -H nautilus
```

navigate to the fstab file, make a copy of it, edit the original with gedit, save and reboot.

---

### Post by ErwinK on 2016-04-10
It seems to be working now. Thank You

---

### Post by howefield on 2016-04-11
> **ErwinK said:**
> It seems to be working now. Thank You

You are welcome, that being the case you could remove the "cdrom" line entirely but with the # sign in place it won't cause you any trouble.

You can now remove the backup fstab file if you wanted to but again it won't cause you any bother other than taking up a tiny piece of disk space.

```
sudo rm /etc/fstab.old
```

---

