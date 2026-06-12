---
title: "[SOLVED] No shared folders or mounting in VMware"
date: 2007-10-29
forum: General Help
---

### Post by Anicka on 2007-10-29
Hi everybody!

I have a problem with my VMware workstation 6.0.0 (Gutsy as a guest in XP). The problem is two-fold: 1) My shared folders from windows are not accessible. This is a big problem for me, so if there is no solution I will have to revert to Feisty. 2) I cannot mount anything from the XP-part of the computer (e.g. iso for VMware tools) It gives an error message: ```
[mntent]: line 9 in /etc/fstab is bad
mount: can't find /media/cdrom0/ in /etc/fstab or /etc/mtab
```
My fstab is:```
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda1 -- converted during upgrade to edgy
UUID=7d52d6eb-efa0-4d29-aa91-f37a49c32dc9 / ext3 defaults,errors=remount-ro 0 1
# /dev/sda5 -- converted during upgrade to edgy
UUID=3f1f18f8-615f-4a1b-aafb-79695cad5054 none swap sw 0 0
/dev/cdrom        /media/cdrom0   udf,iso9660 user,noauto     0       0# Beginning of the block added by the VMware software
.host:/                 /mnt/hgfs               vmhgfs  defaults,ttl=5     0 0
# End of the block added by the VMware software
```
and my mtab is:```
/dev/sda1 / ext3 rw,errors=remount-ro 0 0
proc /proc proc rw,noexec,nosuid,nodev 0 0
/sys /sys sysfs rw,noexec,nosuid,nodev 0 0
varrun /var/run tmpfs rw,noexec,nosuid,nodev,mode=0755 0 0
varlock /var/lock tmpfs rw,noexec,nosuid,nodev,mode=1777 0 0
udev /dev tmpfs rw,mode=0755 0 0
devshm /dev/shm tmpfs rw 0 0
devpts /dev/pts devpts rw,gid=5,mode=620 0 0
lrm /lib/modules/2.6.22-14-generic/volatile tmpfs rw 0 0
securityfs /sys/kernel/security securityfs rw 0 0
none /proc/fs/vmblock/mountPoint vmblock rw 0 0
binfmt_misc /proc/sys/fs/binfmt_misc binfmt_misc rw,noexec,nosuid,nodev 0 0
```
I would think that these two problems are connected, but it is the first part that is the "deal-breaker".

I hope somebody out there have a solution for this problem.

---

### Post by dickohead on 2007-10-29
To access your windows shared folders you will need to install smbfs:
sudo apt-get install smbfs
Then using nautilus go to smb://the.windows.ip.address/ (smb://192.168.1.1) and see if it picks up your shares that way.

As for the CD-Rom, have you told VMware to allow access to it?

---

### Post by Anicka on 2007-10-29
I have found the solution (I think). The problem is that I cannot use it at the moment. I have a too old version of VMWare that doesn't recognise the kernel 2.6.22. If I can convince the IT-support at work to give me an upgrade to 6.0.1 or 6.0.2, the rest of the solution is found here: [http://communities.vmware.com/message/778755](http://communities.vmware.com/message/778755)

Update: Actually taking the tar-file from the forth post worked without updating VMWare.

---

