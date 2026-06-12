---
title: "USB Mount Problems"
date: 2007-12-22
forum: General Help
---

### Post by atkinsonar on 2007-12-22
I just installed Ubuntu 7.10, and am having lots of problems with USB devices.  I have a 4GB Cruzer Micro, which doesn't get recognized.  I also have a Seagate 250GB External USB drive which doesn't get recognized.  Both have absolutely no problems in a Windows environment.

I am not very proficient in the terminal environment, so I am hoping one of you out there can help me out.

I have installed ntfs-3g, and have read just about every post out there regarding this issue.  If nothing else, I know I am not alone.  Please see the results of a common command requested out there, and let me know what else I can provide to help troubleshoot.  I appreciate everyone's input in advance.  This output doesn't seem to change whenever I connect my external HD, or when I disconnect it.


aaron@aaron-laptop:~$ sudo mount
/dev/sda1 on / type ext3 (rw,errors=remount-ro)
proc on /proc type proc (rw,noexec,nosuid,nodev)
/sys on /sys type sysfs (rw,noexec,nosuid,nodev)
varrun on /var/run type tmpfs (rw,noexec,nosuid,nodev,mode=0755)
varlock on /var/lock type tmpfs (rw,noexec,nosuid,nodev,mode=1777)
udev on /dev type tmpfs (rw,mode=0755)
devshm on /dev/shm type tmpfs (rw)
devpts on /dev/pts type devpts (rw,gid=5,mode=620)
lrm on /lib/modules/2.6.22-14-generic/volatile type tmpfs (rw)
securityfs on /sys/kernel/security type securityfs (rw)
/dev/scd0 on /media/cdrom0 type iso9660 (ro,nosuid,nodev,user=aaron)

---Thanks---

---

### Post by viking777 on 2007-12-22
Have you tried this?

[http://ubuntuforums.org/showthread.php?p=3944699#post3944699](http://ubuntuforums.org/showthread.php?p=3944699#post3944699)

---

