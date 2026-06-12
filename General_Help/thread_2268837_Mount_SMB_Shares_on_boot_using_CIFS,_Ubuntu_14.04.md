---
title: "Mount SMB Shares on boot using CIFS, Ubuntu 14.04"
date: 2015-03-11
forum: General Help
---

### Post by mark203 on 2015-03-11
I am trying to mount a few smb shares and the last time I made a mistake that curropted my ability to write to the device from my windows PCs :P - I believe I have the right info - but the problem is I have been mounting it from a terminal on a debian squeeze distro.
Can anyone help me with what my fstab edit should be in order to get these mounts on boot?

```
mount -t cifs //192.168.2.21/Volume_1/Movies /media/Movies -o guest,rw,uid=1000,gid=1000,nounix,iocharset=utf8,filemode=0777,dir_mode=0777
mount -t cifs //192.168.2.22/Volume_1/Movies /media/TV -o guest,rw,uid=1000,gid=1000,nounix,iocharset=utf8,filemode=0777,dir_mode=0777

```
Right now, I added the entries but it looks like I cant get it to automount when I login. It shows up in Nautils but says only root can mount when I try to access it.

My FSCK entries look like:
```

# /etc/fstab: static file system information.
#
# Use 'blkid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
/dev/mapper/futureMedia--vg-root /               ext4    errors=remount-ro 0       1
# /boot was on /dev/sda1 during installation
UUID=6b32e47a-a385-4fd0-8889-12b7ed61ce11 /boot           ext2    defaults        0       2
/dev/mapper/futureMedia--vg-swap_1 none            swap    sw              0       0
# Windows Share for TV
//192.168.2.22/Volume_1/TV  /media/TV  cifs  guest,rw,uid=1000,gid=1000,nounix,iocharset=utf8,filemode=0777,dir_mode=0777,auto   0  0
# Windows Share for Movies
//192.168.2.12/Volume_1/Movies  /media/Movies  cifs  guest,rw,uid=1000,gid=1000,nounix,iocharset=utf8,filemode=0777,dir_mode=0777,auto   0  0
# Windows Share for TV2
//192.168.2.8/Public/Videos /media/TV2  cifs  guest,rw,uid=1000,gid=1000,nounix,iocharset=utf8,filemode=0777,dir_mode=0777,auto   0  0

```
Any ideas how I can make a change to this so that on boot, no matter what user is logged in - these shares will be mounted and ready to go (for a plex streaming server)

---

### Post by TheFu on 2015-03-13
Looks fine to me, but I'd be worried about using a read-write mount with nounix.  That disables file locking and can lead to corruption.
[https://wiki.ubuntu.com/MountWindowsSharesPermanently](https://wiki.ubuntu.com/MountWindowsSharesPermanently) has more detailed help, but it looks like you've got it already.

Have you considered the uid/gid carefully?  Perhaps using the plex uid/gid would be smarter? I dunno. Depends on your situation. If you do, might want to add your userid into the plex group.


Oh ... the target mount points must pre-exist. Do they?
**sudo mkdir -p /media/TV /media/Movies /media/TV2 **

Personally, I wouldn't put a forever-mount under /media, but that is your choice.  /media is where the OS automatically mounts temporary file systems. I'd rather not let the OS (or gvfs) have a chance to screw up my mounts.

---

