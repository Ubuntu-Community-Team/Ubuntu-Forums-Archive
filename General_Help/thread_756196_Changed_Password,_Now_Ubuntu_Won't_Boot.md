---
title: "Changed Password, Now Ubuntu Won't Boot"
date: 2008-04-15
forum: General Help
---

### Post by SupaRice on 2008-04-15
I'm running 2.6.20-16-generic:

So I changed my password last night.  I used the GUI in gnome to do so.  When I came home from work today, I could SSH into my Ubuntu box but couldn't sudo, and SAMBA had stopped working.  So I went to the console and xscreensaver was locked up.  So, I tried restarting X.  When I did that, the machine basically locked up.  So I rebooted it, and now it says:

```
exec: 7: /etc/init.d/rcS: Permission denied
init: rcS main process terminated with status 2
[   60.953221] EXT-fs error (device hda2): ext3_get_inode_loc: unable to read inode block - inode=1599613, block=3211273
exec: 8: /etc/init.d/rc: Permission denied
init: rc2 main process (2468) terminated with status 2
```

The only thing strange about my system is my use of software RAID.

I use a RAID partition for my /home and another for a SAMBA share.  The /home has caused me some minor issues in times past when it would get out of sync because of hardware.  I only mention it because I'm not sure if it's related this time.

Previous issue:
[http://ubuntuforums.org/showthread.php?t=471090]("http://ubuntuforums.org/showthread.php?t=471090")

```

ubuntu@ubuntu:~$ sudo fdisk -l

Disk /dev/hda: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1               1       12158    97659103+  fd  Linux raid autodetect
/dev/hda2           12159       14593    19559137+  83  Linux

Disk /dev/hdc: 122.9 GB, 122942324736 bytes
255 heads, 63 sectors/track, 14946 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hdc1               1         365     2931831   82  Linux swap / Solaris
/dev/hdc2             366       12523    97659135   fd  Linux raid autodetect
/dev/hdc3           12524       14946    19462747+  83  Linux

Disk /dev/sda: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1       30401   244196001   fd  Linux raid autodetect

Disk /dev/sdb: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1       30401   244196001   fd  Linux raid autodetect

```


Help?  I'm in over my head here, and haven't found anything via search that looks like it's the same problem.  I found one other thread where someone was able to use the recovery to issue a passwd {username}, but that doesn't even work for me.  I can get it to go to the recovery "root@(none):~#" prompt, but don't know where to go from there.  I guess I could reinstall, but I'd like to recover this if at all possible.

Thanks for any help in advance.

---

### Post by SupaRice on 2008-04-16
*bump*

---

### Post by SupaRice on 2008-04-18
Anybody?

---

### Post by zvacet on 2008-04-18
Boot in recovery mode and type 

```
passwd username
```

an put your old password again.That is all I can tink of right now.

---

### Post by SupaRice on 2008-04-19
> **zvacet said:**
> Boot in recovery mode and type 

```
passwd username
```

an put your old password again.That is all I can tink of right now.


Yeah, I've tried that and it doesn't work.  It won't find the passwd command.  Any other ideas?

---

