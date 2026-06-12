---
title: "Strange fstab Device names in Edgy"
date: 2006-11-12
forum: General Help
---

### Post by topquarck on 2006-11-12
[SIZE="3"]
hi all;
I upgraded my Dapper to Edgy, every things works will

but when I opened the fstab file i found my partitions named in a very strange way
look at that:
```

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/hda7 -- converted during upgrade to edgy
UUID=25f47723-7a44-4b17-9b8a-e8a11c5fa2ab / ext3 defaults,errors=remount-ro 0 1
# /dev/hda1 -- converted during upgrade to edgy
UUID=8A50027150026473 /media/hda1 ntfs defaults,nls=utf8,umask=007,gid=46 0 1
# /dev/hda6 -- converted during upgrade to edgy
UUID=11FA92E1962117B9 /media/hda6 ntfs defaults,nls=utf8,umask=007,gid=46 0 1
# /dev/hda5 -- converted during upgrade to edgy
UUID=d8a3b650-8897-44b3-bbe3-b7bafcce3077 none swap sw 0 0
/dev/hdb        /media/cdrom0   udf,iso9660 user,noauto     0       0

```
Can anybody tell me whats wrong with that??
it works fine and i can read all data from my windows partitions but why is the strange names?
[SIZE="4"]IS IT Dangerous tp rename partitions to their original names ???[/SIZE]

thanx alot[/SIZE]

---

### Post by bulldog on 2006-11-12
Why should there be anything wrong??

It works fine as you stated,so..............????

---

### Post by IanVaughan on 2006-11-23
Hey, yeah, I'd like to know why its done this?
As it makes editing the file much harder!
Why cant it stay the same!!!!?

---

### Post by therunnyman on 2006-11-23
I'm seeing two questions, right?

Devices are enumerated by UUID now, I think in an effort to make enumeration robust.    Ubuntu will know where it is all the time now, instead of making reference to where it thinks it is, or where it thinks it's supposed to be.

As far as I can tell, changing it back to devices names (eg, sda1 or hda1) doesn't harm the system.  If it should happen something does go wrong, simply go into the Device Manager (Sys>Admin>Device Manager) and grab the UUID from there, and change it back.

runny

---

### Post by jimbob on 2006-11-23
Check out this thread ...

[http://www.ubuntuforums.org/showthread.php?t=278652](http://www.ubuntuforums.org/showthread.php?t=278652)

________________________________       
  If I can't be Mr. Root I won't play ...

[COLOR="Red"][SIZE="2"]*Registered Linux User #400396*[/SIZE][/COLOR]

---

