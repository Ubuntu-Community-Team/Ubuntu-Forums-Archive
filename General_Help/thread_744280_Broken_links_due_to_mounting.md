---
title: "Broken links due to mounting"
date: 2008-04-03
forum: General Help
---

### Post by themuddler on 2008-04-03
I link to several folders on an internal drive on my desktop.  Unfortunately, Ubuntu doesn't mount the drive until I try to access it directly so the links are broken initially (until I access that drive).  Is there a way to encourage it to mount all drives on startup even without my having to access each one?

It seems like it shouldn't be difficult but I couldn't find anywhere to tell me how.  If I really need to do it manually with fstab then just say so and I'll do that, but I'd rather use automatics to avoid introducing errors through my inexperience with fstab.

Thanks in anticipation.

---

### Post by Rocket2DMn on 2008-04-03
A drive that is not present cannot be mounted (like unplugged external drives).  If the drive is internal, the best thing to do is add it to /etc/fstab and it should be mounted on boot.
Here is a guide that I like f you want to try it out - [http://ubuntuforums.org/showthread.php?t=283131](http://ubuntuforums.org/showthread.php?t=283131)
Otherwise, post the output of the following commands here and I'll help you
```
cat /etc/fstab
sudo fdisk -l
```
Please specify which device/partition it is that you are trying to mount (if you know).

---

### Post by themuddler on 2008-04-03
Thanks Rocket.  I'll have a go at doing the fstab bits myself now from that guide.  It's a shame I can't just 'save' the current configuration to fstab though!  I may need a hand if it doesn't work out but I'll have a shot at it.

---

### Post by themuddler on 2008-04-03
Rocket, am I right in thinking that since my drives have already been mounted automatically I can just copy the relevant lines from mtab to fstab?  The formats look very similar.

---

### Post by themuddler on 2008-04-03
mtab
******

/host/ubuntu/disks/root.disk / ext3 rw,errors=remount-ro 0 0
proc /proc proc rw,noexec,nosuid,nodev 0 0
/sys /sys sysfs rw,noexec,nosuid,nodev 0 0
varrun /var/run tmpfs rw,noexec,nosuid,nodev,mode=0755 0 0
varlock /var/lock tmpfs rw,noexec,nosuid,nodev,mode=1777 0 0
udev /dev tmpfs rw,mode=0755 0 0
devshm /dev/shm tmpfs rw 0 0
devpts /dev/pts devpts rw,gid=5,mode=620 0 0
lrm /lib/modules/2.6.24-12-generic/volatile tmpfs rw 0 0
/host/ubuntu/disks/boot /boot none rw,bind 0 0
securityfs /sys/kernel/security securityfs rw 0 0
binfmt_misc /proc/sys/fs/binfmt_misc binfmt_misc rw,noexec,nosuid,nodev 0 0
gvfs-fuse-daemon /home/mud/.gvfs fuse.gvfs-fuse-daemon rw,nosuid,nodev,user=mud 0 0
/dev/sdd1 /media/FILES fuseblk rw,nosuid,nodev,noatime,allow_other,blksize=512 0 0
/dev/sdb5 /media/System fuseblk rw,nosuid,nodev,noatime,allow_other,blksize=4096 0 0
/dev/sda1 /media/CLASSIC\040HD vfat rw,nosuid,nodev,uhelper=hal,shortname=mixed,uid=1000,utf8,umask=077,flush 0 0
/dev/sdb1 /media/OTHER vfat rw,nosuid,nodev,uhelper=hal,shortname=mixed,uid=1000,utf8,umask=077,flush 0 0


fstab
******
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/host/ubuntu/disks/root.disk /               ext3    loop,errors=remount-ro 0       1
/host/ubuntu/disks/boot /boot           none    bind            0       0
/host/ubuntu/disks/swap.disk none            swap    loop,sw         0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0

fdisk -l is quite big but I can post if need be.  Could I almost just cut+paste from one into the other?

---

### Post by themuddler on 2008-04-03
Oh, and it's the last 4 lines of mtab which are the partitions I'm trying to mount on startup.  Thanks for the help

---

### Post by Rocket2DMn on 2008-04-03
I'm assuming the fuseblk partitions are NTFS and that all mount points already exist (otherwise sudo mkdir them)..
```
gksudo gedit /etc/fstab
```
add the lines
```
/dev/sdd1 /media/FILES ntfs-3g defaults,locale=en_US.utf8 0 0
/dev/sdb5 /media/System ntfs-3g defaults,locale=en_US.utf8 0 0
/dev/sda1 /media/CLASSIC\040HD vfat defaults,users,uid=1000,gid=100,umask=007 0 0
/dev/sdb1 /media/OTHER vfat defaults,users,uid=1000,gid=100,umask=007 0 0
```
Those "options" should be adequate for the vfat partitions, but you want to fiddle around with them so they work exactly how you want.
After you add the lines, save and close fstab and run
```
sudo mount -a
```  If you get errors, please post them.

---

### Post by themuddler on 2008-04-03
I'm much obliged to you.  It seemed to work without errors so far.  I'm going to restart the computer to see if this makes the drives mount on start and solves the problem with the links.

Thanks

---

### Post by themuddler on 2008-04-03
It works wonderfully, thanks!  It also means I can get straight into firefox without having to open the drive with my windows profile on - so success all round.  Goes to show that good things can come of editing configuration files, as scary as it seems.

Time for some more refinement.  Cheers.

---

### Post by emre.bag on 2008-04-15
Hi
This is my first day as an ubuntu user and i also have an internal drive which i want auto-mounted.
My mtab reads:

/dev/sdb1 / ext3 rw,relatime,errors=remount-ro 0 0
proc /proc proc rw,noexec,nosuid,nodev 0 0
/sys /sys sysfs rw,noexec,nosuid,nodev 0 0
varrun /var/run tmpfs rw,noexec,nosuid,nodev,mode=0755 0 0
varlock /var/lock tmpfs rw,noexec,nosuid,nodev,mode=1777 0 0
udev /dev tmpfs rw,mode=0755 0 0
devshm /dev/shm tmpfs rw 0 0
devpts /dev/pts devpts rw,gid=5,mode=620 0 0
lrm /lib/modules/2.6.24-16-generic/volatile tmpfs rw 0 0
securityfs /sys/kernel/security securityfs rw 0 0
gvfs-fuse-daemon /home/emre/.gvfs fuse.gvfs-fuse-daemon rw,nosuid,nodev,user=emre 0 0
/dev/sda1 /media/2 fuseblk rw,nosuid,nodev,noatime,allow_other,blksize=4096 0 0

and the last line is the device i'd like mounted.

However i don't really know anything about code or permissions so what line should i add to my fstab?

Thanks

---

### Post by bodhi.zazen on 2008-04-15
assuming it is ntfs and you want read-write access :

```
/dev/sda1 /media/2 ntfs-3g auto,uid=1000,gid=100,fmask=660,dmask=770 0 0
```

Otherwise can you provide more details ? file system ? version of Ubuntu ?

---

### Post by emre.bag on 2008-04-15
i solved it myself
thanks anyway this thread is mighty usefull
i just wish ubuntu did this by default

---

### Post by themuddler on 2008-04-16
It does seem a shame that there's no tool in ubuntu to allow you to make-permanent the volumes which are automounted initially.  It would seem sensible to automate such changes where possible rather than have to edit files having searched the internet and asked on fora.

Should I suggest this to the developers?  Ubuntu could present you with a simplified list originating from mtab, and you could check boxes to indicate what should be added to fstab for you.

---

### Post by emre.bag on 2008-04-21
That would be great.
Here i am using the beta without any linux knowledge at all. And it does work
So why not make it better?

---

