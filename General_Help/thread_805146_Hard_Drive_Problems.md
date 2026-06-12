---
title: "Hard Drive Problems"
date: 2008-05-23
forum: General Help
---

### Post by delsydebothom on 2008-05-23
I know that this question is so basic that I must be overlooking it somewhere, but I need some help accessing my new 350GB hard drive. I used the disk partitioner to format and mount it, but I can't access it because it says that I am not the owner. The computer is, of course, innocently mistaken. What do I need to do to unlock the hard disk when it says permissions cannot be determined? Thanks.

---

### Post by TeoBigusGeekus on 2008-05-23
Post the results of 
```
mount
```

---

### Post by delsydebothom on 2008-05-23
> **TeoBigusGeekus said:**
> Post the results of 
```
mount
```


Hmmm...didn't work. When I try it, the output says:

> /dev/sda1 on / type ext3 (rw,relatime,errors=remount-ro)
proc on /proc type proc (rw,noexec,nosuid,nodev)
/sys on /sys type sysfs (rw,noexec,nosuid,nodev)
varrun on /var/run type tmpfs (rw,noexec,nosuid,nodev,mode=0755)
varlock on /var/lock type tmpfs (rw,noexec,nosuid,nodev,mode=1777)
udev on /dev type tmpfs (rw,mode=0755)
devshm on /dev/shm type tmpfs (rw)
devpts on /dev/pts type devpts (rw,gid=5,mode=620)
lrm on /lib/modules/2.6.24-17-generic/volatile type tmpfs (rw)
securityfs on /sys/kernel/security type securityfs (rw)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw,noexec,nosuid,nodev)
gvfs-fuse-daemon on /home/pugiofidei/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=pugiofidei)
/dev/scd0 on /media/Silent_Hill_PC type iso9660 (ro,nosuid,nodev,uhelper=hal,uid=1000,utf8)
gvfs-fuse-daemon on /home/bethy/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=bethy)
/dev/sdb1 on /media/disk type ext2 (rw,nosuid,nodev,uhelper=hal)

---

### Post by delsydebothom on 2008-05-23
Yikes, double post. Ignore this one.

---

### Post by delsydebothom on 2008-05-23
Ignore the "cool" smiley. He isn't supposed to be there. An 8 is

---

### Post by itaintover on 2008-05-23
what exactly do you get when you try to access /media/disk?

try
sudo umount -l /dev/sdb1
sudo mount /dev/sdb1 /media/disk

---

### Post by delsydebothom on 2008-05-23
> **itaintover said:**
> what exactly do you get when you try to access /media/disk?

try
sudo umount -l /dev/sdb1
sudo mount /dev/sdb1 /media/disk


Well, for the first one, I get:
> sudo: unmount: command not found
For the second, I get:
> mount: can't find /dev/sdb1/media/disk in /etc/fstab or /etc/mtab

---

### Post by omababy on 2008-05-24
You need to change the permissions try:

sudo chown -R root:username /media/disk

Edit:
substitute your login id with username.

You may need to change read/write permissions to, if so:

sudo chmod -R 775 /media/disk

---

### Post by itaintover on 2008-05-24
delsydebothom, just copy and paste what i wrote into your terminal, its umount not unmount and theres space between /dev/sdb1 and /media/disk

do it to be sure it's mounted properly, then try changing permissions like omababy said

---

