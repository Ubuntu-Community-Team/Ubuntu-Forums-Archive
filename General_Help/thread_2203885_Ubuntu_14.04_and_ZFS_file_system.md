---
title: "Ubuntu 14.04 and ZFS file system"
date: 2014-02-05
forum: General Help
---

### Post by zaoka on 2014-02-05
Does Ubuntu 14.04 supports ZFS file system and if not will that be implemented in the future?

I have to build server that stores about 35TB of files and I was told that ZFS is the way to go. What Ubuntu file system would be the best for this application?

---

### Post by grahammechanical on 2014-02-05
Do not expect Ubuntu to support ZFS. Here is the reason why.

> [COLOR=#333333][FONT=Ubuntu Beta]ZFS cannot be added to Linux directly because the CDDL is incompatible with the GPL.  ZFS can, however, be distributed as a DKMS package separate from the main kernel package.[/FONT][/COLOR]

[https://wiki.ubuntu.com/ZFS](https://wiki.ubuntu.com/ZFS)

As with most, if not all, PPAs we have to wait until a new version of Ubuntu is released to see if a PPA will be available for that version.

[https://launchpad.net/~zfs-native/+archive/stable/](https://launchpad.net/~zfs-native/+archive/stable/)

> [COLOR=#000000][FONT=sans-serif]The Free Software Foundation [/FONT][/COLOR][COLOR=#000000][FONT=sans-serif]considers it a free software license [/FONT][/COLOR][COLOR=#000000][FONT=sans-serif]that is incompatible [/FONT][/COLOR][COLOR=#000000][FONT=sans-serif]with the GNU General Public License (GPL).[/FONT][/COLOR]

[http://en.wikipedia.org/wiki/Common_Development_and_Distribution_License](http://en.wikipedia.org/wiki/Common_Development_and_Distribution_License)

Regards.

---

### Post by tgalati4 on 2014-02-05
You need to research the difference between ext4, btfs, and zfs.  35TB is a lot of data, but how is it used?  Video editing, audio editing, home collection of music and videos, lots of small files from developing and compiling code, one user, 12 users?  Just because someone tells you that zfs is the way to go does not mean it is the best filesystem for your use case.

---

### Post by bab1 on 2014-02-05
> **grahammechanical said:**
> Do not expect Ubuntu to support ZFS. Here is the reason why.



[https://wiki.ubuntu.com/ZFS](https://wiki.ubuntu.com/ZFS)

As with most, if not all, PPAs we have to wait until a new version of Ubuntu is released to see if a PPA will be available for that version.

[https://launchpad.net/~zfs-native/+archive/stable/](https://launchpad.net/~zfs-native/+archive/stable/)



[http://en.wikipedia.org/wiki/Common_Development_and_Distribution_License](http://en.wikipedia.org/wiki/Common_Development_and_Distribution_License)

Regards.

ZFS is supported in Linux.  [The ZFS On Linux project provides a ZFS kernel module which you load.]("http://zfsonlinux.org/")  The module isn’t distributed with or statically linked to the kernel so there is no license conflict between the CDDL ZFS code and the GPL Linux kernel code.  This is mentioned in the [Ubuntu WikI ]("https://wiki.ubuntu.com/ZFS").

---

### Post by zaoka on 2014-02-05
About 35 users, its printing company, they want to store files on the server and share files between workstations as well.

Samba & Ubuntu is what I was thinking about before I found that ZFS is the only filesystem that is able to prevent and fix corrupted files on that big amount of data.

I found that Ubuntu can be used with ZFS however I heard that updates may damage it...

Does anybody use ext3 or ext4 or this much of data?

---

### Post by tgalati4 on 2014-02-06
Ext4 should work fine.  ZFS is not a backup system.  Data corruption is rare and zfs requires quite a bit of RAM to function properly.  You could set up both.  A standard ext4 installation with simple data shares to support your workstations then a second server running as a NAS using zfs that provides a nightly backup with checksums and bitrot protection.  One year from now, you can look back and see how many incidents of data corruption and/or problems with ext4.  You will probably have more failures of UPS batteries and power supplies than data corruption.

---

### Post by faultybit on 2014-02-10
Data corruption is not that rare: [http://en.wikipedia.org/wiki/Silent_data_corruption#SILENT](http://en.wikipedia.org/wiki/Silent_data_corruption#SILENT). It is very likely that something like this will happen hosting 35 TB of data and ext4 is not going to help here. I would suggest also to use ECC RAM if it was not already considered.

---

### Post by tgalati4 on 2014-02-10
If you have decent, server-grade hardware, corruption is rare on a per-user basis.  Over the entire enterprise and over several years, yes bit rot can be an issue.  But in this use case I think ext4 will do just fine.  Otherwise, run zfs in its native environment.

---

### Post by lukeiamyourfather on 2014-02-10
> **zaoka said:**
> 
Does Ubuntu 14.04 supports ZFS file system and if not will that be implemented in the future?


Ubuntu itself will never support ZFS out of the box because of license compatibility issues. However the ZFS on Linux project (and/or OpenZFS project) supports Ubuntu in that regard. This is not a big deal but something to be aware of. It would be shocking to me if Ubuntu 14.04 LTS wasn't supported when it's released.

> **zaoka said:**
> 
I found that Ubuntu can be used with ZFS however I heard that updates may damage it...


Since ZFS on Linux is a kernel module it needs to be compiled for the kernel that is going to be used. If the kernel changes (due to something like updates) then the ZFS kernel module has to be recompiled for the new kernel. As of this post I'm writing that happens automatically for you if you install ZFS on Linux through the stable PPA because it's setup to use DKMS (builds kernel modules when the kernel changes). 

[https://launchpad.net/~zfs-native/+archive/stable](https://launchpad.net/~zfs-native/+archive/stable)

> **tgalati4 said:**
> 
A standard ext4 installation with simple data shares to support your workstations then a second server running as a NAS using zfs that provides a nightly backup with checksums and bitrot protection.  


At that point ZFS would provide nothing in terms of preventing silent data corruption, anything that gets borked on the ext4 file system would be replicated to ZFS when backing up. To prevent silent data corruption you use ZFS from the start, not as a backup (though it could be used as a backup from ZFS to ZFS which is what I do).

> **tgalati4 said:**
> 
One year from now, you can look back and see how many incidents of data corruption and/or problems with ext4.  You will probably have more failures of UPS batteries and power supplies than data corruption.

In my experience silent data corruption is quite common with hardware RAID and traditional file systems like ext4, alarmingly so depending on how important that data is. Your mileage may vary. There's an interesting slide about silent data corruption in the classic presentation about ZFS. See slide number 13.

[http://wiki.illumos.org/download/attachments/1146951/zfs_last.pdf](http://wiki.illumos.org/download/attachments/1146951/zfs_last.pdf)

As a general reply to the original poster, I think you're on the right track. There are lots of right answers to accomplish what you want to do. In my opinion ZFS is the best way to go but of course not the only way to go.

---

