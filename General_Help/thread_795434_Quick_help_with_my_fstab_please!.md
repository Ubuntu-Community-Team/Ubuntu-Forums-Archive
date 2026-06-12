---
title: "Quick help with my fstab please!"
date: 2008-05-15
forum: General Help
---

### Post by clintonthegeek on 2008-05-15
Hi everyone!

I've recently removed two older IDE hard drives I had installed in my box, and am left with two SATA drives and my IDE cd-rom drive. Now, every boot drops me to a recovery shell with root permissions in order to let me "fix" my filesystem, since Kubuntu can't find my old hard drives. I can type "exit" to continue booting, but it's a pain.

[img]http://img180.imageshack.us/img180/967/filesystemshq0.png[/img]

That is what KDE reports as my filesystems, which is mostly correct -- though I currently have a CD in my cd-rom drive which is mounted (at /dev/scd0, not /dev/hdd1), so that should say "Enabled" I think. I have no swap partition.

Well, although I have no filesystem hardware starting with 'h'in /dev/ at all, my /etc/fstab mentions a few, so I think that might be causing my boot-up delays. Here's my fstab:

```
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc /proc proc defaults 0 0
# /dev/sda4
UUID=267c33b4-e57e-470a-8537-89e307851a11 / ext3 nouser,defaults,errors=remount-ro,atime,auto,rw,dev,exec,suid 0 1
# /dev/sda1
UUID=c36eb0d2-dc95-4d99-b9dc-bcc60c8eb0c0 /home ext3 nouser,defaults,atime,auto,rw,dev,exec,suid 0 2
# /dev/hdc1
/dev/hdc1 /media/hdc1 ext3 nouser,defaults,atime,auto,rw,dev,exec,suid 0 2
# /dev/hdd1
#UUID=8EA8FD55A8FD3C71 /media/hdd1 ntfs defaults,umask=007,uid=0,gid=46,auto,rw,nouser 0 1
# /dev/sda3
# /dev/sda5
UUID=b543dd8e-6b86-45de-a97a-6a417e944beb none swap sw 0 0
/dev/hda /media/cdrom0 udf,iso9660 user,atime,noauto,rw,dev,exec,suid 0 0
/dev/fd0 /media/floppy0 auto user,atime,noauto,rw,dev,exec,suid 0 0
/dev/hdd1 /media/hdd1 ext3 nouser,defaults,atime,auto,rw,dev,exec,suid 0 2
/dev/sdb1 /media/sdb1 auto users,atime,auto,rw,dev,exec,suid 2 2
```

I figure I should just comment-out the lines starting with /dev/h*, but don't want to screw anything up.

What should I do? :)

---

### Post by chrisccoulson on 2008-05-15
Could you also post the output of
```
sudo blkid
```
Thanks

---

### Post by clintonthegeek on 2008-05-15
```
/dev/sda5: TYPE="swap" UUID="f89574eb-55f4-41de-b9be-51564d962130"
/dev/sda1: UUID="267c33b4-e57e-470a-8537-89e307851a11" SEC_TYPE="ext2" TYPE="ext3"
/dev/sda4: UUID="9604B10404B0E7FF" TYPE="ntfs"
/dev/sdb1: UUID="95846f0e-60a0-4156-8bff-413fdf90cdfb" SEC_TYPE="ext2" TYPE="ext3"
/dev/sda2: UUID="c36eb0d2-dc95-4d99-b9dc-bcc60c8eb0c0" SEC_TYPE="ext2" TYPE="ext3"
```
Ah, that looks familiar. :)

And maybe I do have a swap partition! Huh.. that's silly of me to forget. :P

---

### Post by drs305 on 2008-05-15
Your uuids have changed. To clean up your fstab (sda4-root, sda1-home, and sda5-swap) you can either:
1) change the uuids to match the ones you got when you ran the blkid command
or
2) revert back to the /dev/sdaX convention.
You have to do that for sda1, sda4 and sda5.

That leaves the hdc1, which your computer doesn't recognize. I assume it is now sdb1. You can comment it out if you aren't sure or change it to the uuid or sdb1 designation. You would probably want to change the mount point to something other than hdc1. If you change it, don't forget to create the mount point before booting so that it actually exists.

Make a backup of your current fstab even though it is messed up, just in case.
```
sudo cp /etc/fstab /etc/fstab.backup
```

---

