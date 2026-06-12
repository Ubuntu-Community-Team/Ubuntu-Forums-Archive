---
title: "fsck appears to hang"
date: 2008-07-07
forum: General Help
---

### Post by LazyBoy on 2008-07-07
Last week fsck of my root partition at boot appeared to hang at:

[INDENT]Checking drive /dev/sda5: 0% (stage 0/5, 0/79)[/INDENT]

I forced a reboot off-power (laptop) so fsck was avoided and got to work. Today I was more patient and it's gotten to

[INDENT]Checking drive /dev/sda5: 0% (stage 1/5, 0/79)
/dev/sda5: 222877/1286752 files (1.9% non-contiguous), 1343995/2560950 blocks[/INDENT]

But it's been stuck at this point a long time with **no disk-activity light and no other indication of progress**.  Didn't there use to be an ascii |======> bar?

Also, I read in another thread that ESC should now cancel fsck, and it's not responding to that.  So I'm going to force a reboot again and get to work.

Any idea how to fix this?
LB

Edit: Removing a P.S. about /var/log/fsck/checkroot.  That file is old.

---

### Post by VMC on 2008-07-07
Is the system initializing the 'fsck' by itself or are you doing this somehow. 

I'm not sure how 'fsck' is starting?

---

### Post by LazyBoy on 2008-07-07
It's happening automatically at boot.
Prior to the lines I quoted, it says something like
> Checking root file system
and
> 23 mounts since last check

Thanks,
LB

---

### Post by mcduck on 2008-07-07
Could you post the contents of your /etc/fstab here? There could be something wrong with fstab's settings for fsck.

Also you could try running fsck manually, just to see what happens..

---

### Post by LazyBoy on 2008-07-07
$ cat /etc/fstab
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc /proc proc defaults 0 0
# /dev/sda5
UUID=2d4163a6-9787-43c1-b437-0464af86a4d0 / ext3 nouser,defaults,errors=remount-ro,atime,auto,rw,dev,exec,suid 0 1
# /dev/sda7
UUID=9fa886ac-5e2f-4416-a9d5-76f61d781c61 /home ext3 nouser,defaults,atime,auto,rw,dev,exec,suid 0 2
# /dev/sda1
UUID=2650B8A850B8805B /media/sda1 ntfs defaults,umask=007,uid=0,gid=46,auto,rw,nouser 0 1
# /dev/sda2
UUID=3432BDB232BD7A06 /media/sda2 ntfs defaults,umask=007,uid=0,gid=46,auto,rw,nouser 0 1
# /dev/sda6
UUID=3126842a-3113-45ac-98b6-daf583682627 none swap sw 0 0
/dev/scd0 /media/cdrom0 auto user,atime,noauto,rw,dev,exec,suid 0 0
//mastershake/music     /media/hmusic   smbfs   auto,credentials=/root/.credentials,uid=1000,umask=000,user,soft   0 0
//mastershake/troy /home/troy/mastershake smbfs auto,credentials=/root/.credentials,uid=1000,umask=000,user,soft   0 0
//mastershake/media /home/troy/mmedia smbfs     auto,credentials=/root/.credentials,uid=1000,umask=000,user,soft   0 0



As for running fsck by hand, I'll need a LiveCD, since this is my root partition, yes?

Thanks,
LB

---

### Post by danwood76 on 2008-07-07
No you can run fsck in recovery mode on your root partition.

If it wants to run the fsck it will also run this upon boot in recovery mode.

---

### Post by mcduck on 2008-07-07
OK, I think this might be the problem: There are several partitions with the fsck option set to "1", while it should be used for root partition only and all others should have either "2" (to check them after root) or "0" (to disable fsck on that partition).

Having many partitions set to "1" might confuse fsck.

Try changing the fsck option for your ntfs partitions to something else than "1" I'm not sure if fsck can even do anything for ntfs so I suggest "0":
```
# /etc/fstab: static file system information.
#
# <file system> <mount point> <type> <options> <dump> <pass>
proc /proc proc defaults 0 0
# /dev/sda5
UUID=2d4163a6-9787-43c1-b437-0464af86a4d0 / ext3 nouser,defaults,errors=remount-ro,atime,auto,rw,dev,exec,suid 0 1
# /dev/sda7
UUID=9fa886ac-5e2f-4416-a9d5-76f61d781c61 /home ext3 nouser,defaults,atime,auto,rw,dev,exec,suid 0 2
# /dev/sda1
UUID=2650B8A850B8805B /media/sda1 ntfs defaults,umask=007,uid=0,gid=46,auto,rw,nouser 0 0
# /dev/sda2
UUID=3432BDB232BD7A06 /media/sda2 ntfs defaults,umask=007,uid=0,gid=46,auto,rw,nouser 0 0
# /dev/sda6
UUID=3126842a-3113-45ac-98b6-daf583682627 none swap sw 0 0
/dev/scd0 /media/cdrom0 auto user,atime,noauto,rw,dev,exec,suid 0 0
//mastershake/music /media/hmusic smbfs auto,credentials=/root/.credentials,uid=1000,umask=000,user,soft 0 0
//mastershake/troy /home/troy/mastershake smbfs auto,credentials=/root/.credentials,uid=1000,umask=000,user,soft 0 0
//mastershake/media /home/troy/mmedia smbfs auto,credentials=/root/.credentials,uid=1000,umask=000,user,soft 0 0
```

---

### Post by Tomatz on 2008-07-07
To force a fsck check simply open a terminal and type:

```
sudo touch /forcefsck
```

Reboot ;)

---

### Post by LazyBoy on 2008-07-07
Edit:

Ugh.  My previous theory (deleted) was all wrong.
I was booting a very old (7.10?) kernel and the problem stopped when I fixed that.

Thanks all,
LB

---

