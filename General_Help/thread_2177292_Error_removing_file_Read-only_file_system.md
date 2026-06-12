---
title: "Error removing file: Read-only file system"
date: 2013-09-28
forum: General Help
---

### Post by Justin_Davidson on 2013-09-28
Error removing file: Read-only file system i plugged in a friends thumb drive to share some movies with him and i got an error when transferring and i simply tried to delete them and try to download again got Error removing file: Read-only file system when i tried to delete the files...  I think it is mounted on dev/sda1 i get this when i type mount


/dev/sda1 on / type ext4 (rw,errors=remount-ro)
proc on /proc type proc (rw,noexec,nosuid,nodev)
sysfs on /sys type sysfs (rw,noexec,nosuid,nodev)
none on /sys/fs/cgroup type tmpfs (rw)
none on /sys/fs/fuse/connections type fusectl (rw)
none on /sys/kernel/debug type debugfs (rw)
none on /sys/kernel/security type securityfs (rw)
udev on /dev type devtmpfs (rw,mode=0755)
devpts on /dev/pts type devpts (rw,noexec,nosuid,gid=5,mode=0620)
tmpfs on /run type tmpfs (rw,noexec,nosuid,size=10%,mode=0755)
none on /run/lock type tmpfs (rw,noexec,nosuid,nodev,size=5242880)
none on /run/shm type tmpfs (rw,nosuid,nodev)
none on /run/user type tmpfs (rw,noexec,nosuid,nodev,size=104857600,mode=0755)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw,noexec,nosuid,nodev)
gvfsd-fuse on /run/user/davidson/gvfs type fuse.gvfsd-fuse (rw,nosuid,nodev,user=davidson)
/dev/sdb1 on /media/davidson/387E-C2AA type vfat (ro,nosuid,nodev,uid=1000,gid=1000,shortname=mixed,dmask=0077,utf8=1,showexec,flush,uhelper=udisks2)









i also tryed this command sudo mount -o remount,rw /media/davidson/387E-C2AA dont know if im using it the right way though im very new at this any help would be great its got some important files from work on it then i get this
mount: cannot remount block device /dev/sdb1 read-write, is write-protected

---

### Post by SeijiSensei on 2013-09-28
> mount: cannot remount block device /dev/sdb1 read-write, is write-protected 

Sounds like the device itself is write-protected.  Any physical switches on it?

---

### Post by 3rdalbum on 2013-09-28
If the device has been mounted read-only, it's because there is filesystem damage. You need to use "fsck" on it to repair the filesystem.

If this is an NTFS drive, or the fsck doesn't work, the only remaining option is to reformat the disk so a new filesystem gets created.

---

### Post by SeijiSensei on 2013-09-28
It's formatted with FAT32.  Try running "sudo fsck -t vfat /dev/sdb1" and see if that helps.

---

### Post by Justin_Davidson on 2013-09-28
thanks i tryed all of the above and when i try to reformat with gparted i get Unable to open /dev/sdb read-write (Read-only file system).  /dev/sdb has been opened read-only.

---

