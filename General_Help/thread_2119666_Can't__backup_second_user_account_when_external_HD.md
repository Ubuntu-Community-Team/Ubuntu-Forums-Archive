---
title: "Can't  backup second user account when external HD has changed to /media/myusername"
date: 2013-02-24
forum: General Help
---

### Post by utherpendragonfly on 2013-02-24
I'm very confused. It seems a recent update has changed the mount point  /media/Back-up (an external HD) to /media/my_username/Back-up. So I am unable to backup my wife's data from her second user account.
I changed the backup path (I'm using Grsync) for me so that Grsync now works. But when I switch to my wife's desktop and try to backup, she doesn't have permission any more. Why on earth did they change the /media mount point, anyway? Backups were a breeze before. It's as if they only want a single person to use a computer! 
Can I chown for her through /media/my_username/Back-up/her_username? Won't that totally screw up my permissions?
Help!

---

### Post by zero2xiii on 2013-02-24
Hay,

Check your fstab file for the mount point on the drive:
```
cat /etc/fstab
```

Also you can chown the drive. But that will cause issues. Rather chown her own directory etc:
user1 = /media/backup/user1
user2 = /media/backup/user2

```
chown -R /media/backup/user2 user2:user2
```

This should give user2 write permission to that path.. 

Good luck. But check your mount options FIRST

---

### Post by utherpendragonfly on 2013-02-24
> **zero2xiii said:**
> Hay,

Check your fstab file for the mount point on the drive:
```
cat /etc/fstab
```

Also you can chown the drive. But that will cause issues. Rather chown her own directory etc:
user1 = /media/backup/user1
user2 = /media/backup/user2

```
chown -R /media/backup/user2 user2:user2
```

This should give user2 write permission to that path.. 

Good luck. But check your mount options FIRST

Thanks for the response. This is what I got, but not sure what it means. I don't have '/media/Back-up' anymore, just '/media/'my_username'/Back-up

&#9492;&#9472;> cat /etc/fstab
# /etc/fstab: static file system information.
#
# Use 'blkid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda1 during installation
UUID=36d9d543-9df5-4a3f-9fb7-66252a079fe4 /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda2 during installation
UUID=55b7bfc4-3726-416e-8d93-22c8eb26dddd none            swap    sw              0       0
/dev/sda3 /home/davey/data ext4 defaults 0 1&#9484;&#9472;( davey ) - ( 3.2.0-38-generic ) - ( ~ )

---

### Post by utherpendragonfly on 2013-02-27
I've spent several hours trying to find out how to fix this without success. I've created symbolic links and changed permissions and a few other suggestions I've stumbled across, but nothing works! When I try to open 'Back-up' external drive in second user account, a dialog asks what application I want to open 'symbolic link' with. I chose Thunar, but nothing happens.
This is really frustrating not being able to run a simple back-up for the second user, when it's worked fine for years. Why did someone think this was a good idea? It really seems like they want Ubuntu-based distro users to be limited to one user per computer.
Does anyone have a solution? Has this only happened to me?? I don't know how else to word a search for an answer.

---

