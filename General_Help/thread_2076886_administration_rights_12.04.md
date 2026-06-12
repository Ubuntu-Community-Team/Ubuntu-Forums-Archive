---
title: "administration rights 12.04"
date: 2012-10-27
forum: General Help
---

### Post by meharts on 2012-10-27
Hi folks!
OK! seem to be having admin rights for a drive, directories, subdirectories etc...

I run gksudo nautilus and changed the rights for the drive in question and the subdirectories, but I am still getting blocked by "root".

On this drive I have a directory films and in that directories with the film names and they are all now owned by user instead of root...but all the avi's in those film directories are still owned by root....it doesn't help even checking each film/directory and making sure they have user privileges....the films are still root ownned?!

Of course I can change each and everyone manually from gksudo nautilus....but there are hundereds....help!


How do I get around this?


Thanks as always!

meharts

---

### Post by CharlesA on 2012-10-27
What file system do those files reside on?

---

### Post by meharts on 2012-10-27
Hi CharlesA
Sorry, bit remiss of me...lol

They are on ext4

meharts

---

### Post by grahammechanical on 2012-10-27
Were you root when you created those files? On Ubuntu we use the sudo command to give us temporary root privileges. It is possible to set ourselves up as a root user. Any files created while in the root session will be owned by root.

You could try copying those files as a standard user to another folder and then those copied files might become owned by the standard user and not as root.

There is also a terminal command that can change the permissions and if used with * option all the files in the folder will be changed. I am not familiar with the terminal command to do this.

Regards.

Regards.

---

### Post by meharts on 2012-10-27
Hi grahammechanical!
I just added the drive after installation and formated it to ext4 the files are copied from a ntfs drive....
Tried creating a new directory and moving stuff....nada...

meharts

---

### Post by CharlesA on 2012-10-27
Run this please:

```
mount
```

---

### Post by meharts on 2012-10-27
Hi again!

```


pelle@pelle-PX682AA-B1U-d4060-se:~$ mount
/dev/sda1 on / type ext4 (rw,errors=remount-ro)
proc on /proc type proc (rw,noexec,nosuid,nodev)
sysfs on /sys type sysfs (rw,noexec,nosuid,nodev)
none on /sys/fs/fuse/connections type fusectl (rw)
none on /sys/kernel/debug type debugfs (rw)
none on /sys/kernel/security type securityfs (rw)
udev on /dev type devtmpfs (rw,mode=0755)
devpts on /dev/pts type devpts (rw,noexec,nosuid,gid=5,mode=0620)
tmpfs on /run type tmpfs (rw,noexec,nosuid,size=10%,mode=0755)
none on /run/lock type tmpfs (rw,noexec,nosuid,nodev,size=5242880)
none on /run/shm type tmpfs (rw,nosuid,nodev)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw,noexec,nosuid,nodev)
gvfs-fuse-daemon on /home/pelle/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=pelle)
/dev/sdb1 on /media/Backup_Pelle type ext4 (rw,nosuid,nodev,uhelper=udisks)
gvfs-fuse-daemon on /root/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev)
pelle@pelle-PX682AA-B1U-d4060-se:~$ 



```
Backup_Pelle is the hard drive in question.



meharts

---

