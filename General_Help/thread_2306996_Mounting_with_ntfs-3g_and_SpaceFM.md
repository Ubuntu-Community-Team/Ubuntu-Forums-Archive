---
title: "Mounting with ntfs-3g and SpaceFM"
date: 2015-12-21
forum: General Help
---

### Post by os2 on 2015-12-21
I have a ntfs partition which I would like to automatically mount and use in SpaceFM.

The native Linux ntfs driver allows this to be done without any further authorisation in SpaceFM using the following fstab entry and using the mount command:

```

UUID=...                           /media/disk     ntfs noauto,gid=46,users,umask=007                   0       0

```

However the native ntfs driver doesn't allow writing to the partition. For this I have to use ntfs-3g instead. Having done this, is there a way to get SpaceFM to mount the partition rwx in SpaceFM without authorisation?

I've already tried this fstab entry but I still need to authorise mount using sudo.

```

UUID=...                           /media/disk     ntfs-3g noauto,gid=46,users,umask=007                   0       0

```

---

### Post by ajgreeny on 2015-12-21
It's a long time since I have had an ntfs partition to use and several possible answers are at [http://askubuntu.com/questions/113733/how-do-i-correctly-mount-a-ntfs-partition-in-etc-fstab](http://askubuntu.com/questions/113733/how-do-i-correctly-mount-a-ntfs-partition-in-etc-fstab)

I think either of the following lines in fstab should also work but these are probably a bit older than some of the info on the above link.
UUID=...... /media/disk    ntfs-3g        auto,user,rw 0 0
UUID=...... /media/disk  ntfs    defaults    0    0

I don't think the file-manager you use should make any difference to the mount situation, so I believe that spacefm is irrelevant to your problem.

---

### Post by Morbius1 on 2015-12-21
> **os2 said:**
> However the native ntfs driver doesn't allow writing to the partition. For this I have to use ntfs-3g instead.
I don't quite understand that comment since:
> tester1@vubuntu1404:~$ ls -l /sbin/mount.ntfs
lrwxrwxrwx 1 root root 13 Apr 18  2014 /sbin/mount.ntfs -> mount.ntfs-3g
ntfs and ntfs-3g are linked so there should be no difference which one you call.
> I've already tried this fstab entry but I still need to authorise mount using sudo.
```

UUID=...  /media/disk     ntfs-3g noauto,gid=46,users,umask=007                   0       0
```
Because the "user" and "users" options have no meaning in ntfs/ntfs-3g.
> Having done this, is there a way to get SpaceFM to mount the partition rwx in SpaceFM without authorisation?
> I have a ntfs partition which I would like to automatically mount and use in SpaceFM.
  Confused again. If you want it to automount why are you using the "noauto" option which tells the system not to mount the partition automatically at boot.

Not familiar with SpaceFM so I don't know if it's doing something that other file managers are not which may be why I'm confused.

---

### Post by os2 on 2015-12-21
ntfs is the native kernel driver and ntfs-3g is an extension to this  driver which allows rw. The ntfs kernel driver alone only allows ro.

When  you install ntfs-3g it works as an extension to ntfs and for  convenience the executable filenames are linked. The permissions are 777  but the actual mounting still needs permission. That's where the ntfs  driver provides the 'users' option to do it automatically.

Now if you try and do # /sbin/mount.ntfs /dev/sda2 /media/disk this is what I get:

```

/sbin/mount.ntfs /dev/sda2 /media/disk
Error opening '/dev/sda2': Permission denied
Failed to mount '/dev/sda2': Permission denied
Please check '/dev/sda2' and the ntfs-3g binary permissions,
and the mounting user ID. More explanation is provided at
http://tuxera.com/community/ntfs-3g-faq/#unprivileged

```


Edit. noauto is simply not to mount at boot time. That's fine, I would still like a user in gid mentioned to mount the disk rwx at a later stage without having to supply authorisation.

---

### Post by Morbius1 on 2015-12-21
> **os2 said:**
> Now if you try and do # /sbin/mount.ntfs /dev/sda2 /media/disk this is what I get:

```

/sbin/mount.ntfs /dev/sda2 /media/disk
Error opening '/dev/sda2': Permission denied
Failed to mount '/dev/sda2': Permission denied
Please check '/dev/sda2' and the ntfs-3g binary permissions,
and the mounting user ID. More explanation is provided at
http://tuxera.com/community/ntfs-3g-faq/#unprivileged

```
And if you were to run that command sequence in Ubuntu it would tell you exactly what you need to do to resolve your situation:
> Unprivileged user can not mount NTFS block devices using the external FUSE
library. Either mount the volume as root, or rebuild NTFS-3G with integrated
FUSE support and make it setuid root. Please see more information at
[http://tuxera.com/community/ntfs-3g-faq/#unprivileged](http://tuxera.com/community/ntfs-3g-faq/#unprivileged)
> Edit. noauto is simply not to mount at boot time. That's fine, I would still like a user in gid mentioned to mount the disk rwx at a later stage without having to supply authorisation.
With the gid=46 and that umask only users who are members of the plugdev group will be able to access the partition. It has nothing to do with who can mount it. You aren't going to be able to make it possible for an ordinary user to mount the partition in fstab with the user/users option since it will not work with ntfs - at least not by default:
[http://www.tuxera.com/community/ntfs-3g-faq/#useroption2](http://www.tuxera.com/community/ntfs-3g-faq/#useroption2)
> **Why don&#8217;t the &#8216;user&#8217; and &#8216;users&#8217; options work in /etc/fstab?**
 The &#8216;mount&#8217; command doesn&#8217;t invoke the ntfs-3g binary with the needed  privilege after it has checked and approved the user is entitled to  mount a given device on a specified mount point, hereby the user can&#8217;t  open the device he got the approval in /etc/fstab. This is a problem in  the &#8216;mount&#8217; utility.
 Solution: Use at least NTFS-3G 1.2506 with [setuid-root]("http://www.tuxera.com/community/ntfs-3g-faq/#useroption") set and make sure the user has access rights to the volume and mount point.

Why not just have the partition automount at boot.

---

### Post by Morbius1 on 2015-12-21
Or how about a nice udsks2 mount:
> tester1@vubuntu1410:~$ [COLOR=#0000cd]**udisksctl mount -b /dev/sda5**[/COLOR]
Mounted /dev/sda5 at /media/tester1/DataN
tester1@vubuntu1410:~$ ls -al /media/tester1
total 14
drwxr-x---+ 4 root    root    4096 Dec 21 16:46 .
drwxr-xr-x  9 root    root    4096 Nov 27 12:07 ..
[COLOR=#0000cd]**drwx------  1 tester1 tester1**[/COLOR] 4096 Mar 17  2014 DataN

EDIT: If you are running a very old operation system perhaps not even Ubuntu and udisks2 isn't on your system then revert to udisks:
> tester1@vmintcin13 ~ $ [COLOR=#0000cd]**udisks --mount /dev/sda5**[/COLOR]
Mounted /org/freedesktop/UDisks/devices/sda5 at /media/DataN
tester1@vmintcin13 ~ $ ls -al /media
total 24
drwxr-xr-x  6 root  root   4096 Dec 21 17:40 .
drwxr-xr-x 25 root  root   4096 Jan 10  2015 ..
[COLOR=#0000cd]**drwx------  1 tester1 tester1**[/COLOR]  4096 Sep 14  2012 DataN
Mint13 ( i.e., Ubuntu 12.04 ) is the oldest thing I have left in VBox.

---

### Post by os2 on 2015-12-21
Udisks2 is the default way to do it in both Debian/Ubuntu. On a fresh install of either you don't have any problems mounting NTFS partitions rw without authorisation because Udisks2 is installed and used by default.

The exception here is that I'm not using any system wide privileges such as Policy Kit which is a dependency for Udisks2.

I should mention that pmount also works without policykit.
Ideally just an appropriate use of sudo at the right place with password exemption also works.

I'd be curious to look at any further suggestions.

---

### Post by os2 on 2015-12-21
I set the following standard commands in SpaceFM to mount and unmount respectively:

```

sudo /bin/mount %v
sudo /bin/umount %v

```

and then defined a new file /etc/sudoers.d/mount

```

%plugdev                ALL=(ALL) NOPASSWD: /bin/mount,/bin/umount

```

I am happy with the result.

/etc/fstab

```

UUID=...                           /media/disk     ntfs-3g noauto,gid=46,users,umask=007                   0       0

```

No need to use pmount, Udisks, much less policykit or systemd for that matter.

Thanks for a great discussion.

---

### Post by Morbius1 on 2015-12-22
This is just a suggestion but based on your posts:
> However the native ntfs driver doesn't allow writing to the partition.
...
The exception here is that I'm not using any system wide privileges such as Policy Kit which is a dependency for Udisks2.
You either aren't running Ubuntu, are running a very old version of Ubuntu, or you built Ubuntu from source and decided to make it unique.

In future posts you might want to tell people what operating system and at what level  you are running it or how you built it in order to get a more personalized response.

---

