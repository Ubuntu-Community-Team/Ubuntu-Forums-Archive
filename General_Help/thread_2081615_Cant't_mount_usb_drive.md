---
title: "Cant't mount usb drive"
date: 2012-11-07
forum: General Help
---

### Post by CardCaptor on 2012-11-07
[COLOR=RoyalBlue][B][SIZE=3]Hi i'[SIZE=3]m very new in the community and i'm ha[SIZE=3]ving some problems.

[SIZE=3]I used to make a backup [SIZE=3]with rsynck in an external hard disk conected [SIZE=3]by usb.

[SIZE=3][SIZE=3]Ubuntu stoped mounting it automat[SIZE=3]ically, and i [SIZE=3]can't mount it[SIZE=3].

[SIZE=3]Here [SIZE=3]is m[SIZE=3]y fstab:

[SIZE=2][COLOR=Black]# /etc/fstab: static file system information.
#
# Use 'blkid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda1 during installation
UUID=a830e346-e382-4c31-8daa-1d961a1680c6 /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda5 during installation
UUID=9a70b76f-d0cb-46a2-bea7-91cfa368d788 none            swap    sw              0       0

//FECESCOR-PCOOP/ProCoop /mnt/ProCoop cifs noauto,user,username=ServProCoop,password=lugones24 0 0

[COLOR=RoyalBlue][SIZE=3]Here is my[SIZE=3] [SIZE=3]the return that the console gives me w[SIZE=3]hen i type mount

[SIZE=3][SIZE=2][COLOR=Black]/dev/sda1 on / type ext4 (rw,errors=remount-ro)
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
none on /run/user type tmpfs (rw,noexec,nosuid,nodev,size=104857600,mode=0755)
gvfsd-fuse on /run/user/fecescor/gvfs type fuse.gvfsd-fuse (rw,nosuid,nodev,user=fecescor)
gvfsd-fuse on /root/.gvfs type fuse.gvfsd-fuse (rw,nosuid,nodev)
/dev/sdc1 on /media/fecescor/Verbatim HDD type fuseblk (rw,nosuid,nodev,allow_other,default_permissions,blksize=4096)

[COLOR=RoyalBlue][SIZE=3]I'm also having troble mounting //FE[SIZE=3]C[/SIZE]ESCOR-PCOOP[/SIZE][/COLOR][SIZE=2] [COLOR=RoyalBlue][SIZE=3]which is the last line in fstab. Also [SIZE=3]it's a network location[SIZE=3].[/SIZE] [SIZE=3]I[/SIZE] have created the mounting point but it doesn't mount it.

[SIZE=3]I'm sorry if i posted this in the wrong section, i[SIZE=3]t seems to me that was the right one, and i'm sorry for my gramatical errors english it's no my native language.[/SIZE][/SIZE]
[/SIZE][/SIZE][/COLOR][/SIZE][/COLOR][/SIZE][/SIZE][/SIZE][/SIZE][/SIZE][/SIZE][/COLOR][/COLOR][/SIZE][/SIZE][/SIZE][/SIZE][/SIZE][/SIZE][/SIZE][/SIZE][/SIZE][/SIZE][/SIZE][/SIZE][/SIZE][/SIZE][/SIZE][/B][/COLOR]

---

