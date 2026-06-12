---
title: "can't copy from cd/dvd"
date: 2007-08-05
forum: General Help
---

### Post by darkhut on 2007-08-05
ubuntu mounts the media in ro mode, and that's normal, right? but y can't I copy those files anywhere? when I try from bash I get 

# cp /media/cdrom/* /install/
cp: omitting directory `/media/cdrom/bin'
cp: omitting directory `/media/cdrom/casper'
cp: omitting directory `/media/cdrom/disctree'
cp: omitting directory `/media/cdrom/dists'
cp: omitting directory `/media/cdrom/install'
cp: omitting directory `/media/cdrom/isolinux'
cp: omitting directory `/media/cdrom/pics'
cp: omitting directory `/media/cdrom/pool'
cp: omitting directory `/media/cdrom/preseed'
cp: omitting directory `/media/cdrom/programs'
cp: omitting directory `/media/cdrom/ubuntu'

output from mount -l is:

# mount -l
/dev/sdb3 on / type ext3 (rw,errors=remount-ro) []
proc on /proc type proc (rw,noexec,nosuid,nodev)
/sys on /sys type sysfs (rw,noexec,nosuid,nodev)
varrun on /var/run type tmpfs (rw,noexec,nosuid,nodev,mode=0755)
varlock on /var/lock type tmpfs (rw,noexec,nosuid,nodev,mode=1777)
procbususb on /proc/bus/usb type usbfs (rw)
udev on /dev type tmpfs (rw,mode=0755)
devshm on /dev/shm type tmpfs (rw)
devpts on /dev/pts type devpts (rw,gid=5,mode=620)
lrm on /lib/modules/2.6.20-16-generic/volatile type tmpfs (rw)
/dev/sdb1 on /media/sda1 type ntfs (rw,nls=utf8,umask=007,gid=46) []
/dev/sdb4 on /mnt type ext3 (rw) []
none on /proc/bus/usb type usbfs (rw,devgid=46,devmode=664)
nfsd on /proc/fs/nfsd type nfsd (rw)
rpc_pipefs on /var/lib/nfs/rpc_pipefs type rpc_pipefs (rw)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw)
/dev/hdc on /media/cdrom0 type iso9660 (ro,noexec,nosuid,nodev,user=deedee) [Ubuntu 7.04 i386]

output from df -h:

# df -h
Filesystem            Size  Used Avail Use% Mounted on
/dev/sdb3              19G   16G  1.5G  92% /
varrun                506M  228K  506M   1% /var/run
varlock               506M     0  506M   0% /var/lock
udev                  506M  112K  506M   1% /dev
devshm                506M     0  506M   0% /dev/shm
lrm                   506M   33M  473M   7% /lib/modules/2.6.20-16-generic/volatile
/dev/sdb1              14G  9.8G  4.2G  71% /media/sda1
/dev/sdb4              37G  8.3G   27G  25% /mnt
/dev/hdc              698M  698M     0 100% /media/cdrom0

---

### Post by nitro_n2o on 2007-08-05
```
cp -r /media/cdrom/* /install/
``` 
you need the -r switch to copy directories :)

---

