---
title: "slave drives suddenly became read-only"
date: 2006-12-01
forum: General Help
---

### Post by wgscott on 2006-12-01
This is odd.  One of my grad students was using an account on our Edgy installation that has one main drive and two "slave" drives.  It has been configured this way for at least 2 years with no problems.  Suddenly he could not write to the disk, and to make a long story short, both drives were recognized as read-only until I rebooted the system.

Any idea what could have happened or what to check?
 
 
 I fscked everything (not sure that it is a verb, less sure even that it is a polite one) and rebooted, and it seems to be ok now.
 
 We were running Xubuntu but the problem persisted with KDE, so I think it was a fairly low-level glitch.

---

### Post by taurus on 2006-12-01
What are the output of these two commands from a terminal then?

```
cat /etc/fstab
df -h
```

---

### Post by wgscott on 2006-12-01
Ok, this is quite odd.  It looks like some auto-editing took place.

So, just to try to anticipate some confusion:

I have three disks.  The master disk has a root partition (/dev/hdc1) and then a second partition I call /home (/dev/hdc2 ) There are two slaves, one is /mnt/data_disk1 (/dev/sda1 ) and the other /mnt/data_disk2 (/dev/sdb1 )

I then have a bunch of nfs and samba mounts.  Looks like the latter aren't mounting (separate problem I guess.)
Apart from that the output of df looks ok:

```

-% df
Filesystem           1K-blocks      Used Available Use% Mounted on
/dev/hdc1             19228276  12735756   5515772  70% /
varrun                  517504       116    517388   1% /var/run
varlock                 517504         4    517500   1% /var/lock
procbususb               10240       120     10120   2% /proc/bus/usb
udev                     10240       120     10120   2% /dev
devshm                  517504         0    517504   0% /dev/shm
lrm                     517504     18132    499372   4% /lib/modules/2.6.17-10-386/volatile
xanana.somewhere:/Volumes/Delilah
                     120496248 101302576  19193672  85% /nfs/Delilah
/dev/hdc2            173063520  84023756  80248596  52% /home
/dev/sda1            139058608  40157160  91837672  31% /mnt/data_disk1
/dev/sdb1            141122196 126809324   7144272  95% /mnt/data_disk2
xanana.somewhere:/Volumes/Sampson
                     120617888  96110320  24507568  80% /nfs/Sampson
marcos.somewhere:/Volumes/disk2
                      60045664  39740928  20304736  67% /nfs/disk2
xanana.somewhere:/Users
                     120616040  75172552  45187488  63% /nfs/xanana

```

I'm 99% confident the upgrade messed up the /etc/fstab (sorry I missed this, so thanks for suggesting it).  In any case it is a heinous mess...   All the stuff with UUID and "converted during edgy upgrade" was not put in there by me!

I'm just going to redo this manually.  It looks like I have multiple competing attempts to mount the slave drives.  Arrggh.



```

% cat /etc/fstab
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/hdc1 -- converted during upgrade to edgy
UUID=42459227-e52a-41f6-a8e1-55200ccb05f3 / ext3 defaults,errors=remount-ro 0 1
# /dev/hdc2 -- converted during upgrade to edgy
UUID=2656de2e-247e-4de8-9131-f6f0c55a211c /home ext3 defaults 0 2
#/dev/sda1       /diska          ext2    defaults        0       2
#/dev/sdb1       /diskb          ext2    defaults        0       2
#/dev/sda1        /diska          auto    defaults       0       0
#/dev/sdb1       /mnt/data_disk2  ext3    defaults       0       0
#/dev/sda2               swap                    swap    defaults        0 0
/dev/hda        /media/cdrom0   udf,iso9660 unhide,ro,user,noauto  0       0
/dev/fd0        /media/floppy0  auto    unhide,rw,user,noauto  0       0
#
# Samba mounts from xray123 (raxis computer)
#
\xray239Vrielinklab   /smb/Firstlab   smbfs   timeo=5,auto,credentials=/etc/samba/xray239 0 0 
\xray239Scottlab      /smb/Secondlab         smbfs   timeo=5,auto,credentials=/etc/samba/xray239 0 0
\xray239Juricalab     /smb/Thirdlab       smbfs   timeo=5,auto,credentials=/etc/samba/xray239 0 0
\xray239Nollerlab     /smb/Fourthlab       smbfs   timeo=5,auto,credentials=/etc/samba/xray239 0 0

# NFS mounts from various other computers. OS X has a bug requiring nfsvers2
# <server-host>:</path/to/shared/directory> </local/mount/point> nfs <options> 0 0
xanana.somewhere:/Volumes/Delilah    /nfs/Delilah   nfs  nfsvers=2,soft,timeo=5  0 0
xanana.somewhere:/Volumes/Sampson    /nfs/Sampson   nfs  nfsvers=2,soft,timeo=5  0 0
marcos.somewhere:/Volumes/disk2    /nfs/disk2       nfs  soft,timeo=5  0 0
xanana.somewhere:/Users              /nfs/xanana    nfs  nfsvers=2,soft,timeo=5  0 0
#vanunu.somewhere:/Volumes/400GB_seagate /nfs/400GB_seagate nfs soft,timeo=5  0 0 

# These are the two subsidiary hard drives
# /dev/sda1 -- converted during upgrade to edgy
UUID=a4491577-bec5-4533-961f-39e894f7cfc1 /mnt/data_disk1 ext3 defaults 0 0
# /dev/sdb1 -- converted during upgrade to edgy
UUID=5e0a8ecd-ccb5-4c85-b4fa-7b5a2a9dbe97 /mnt/data_disk2 ext3 defaults 0 0
# Swap space (Denzo needs this)
# /dev/sda2 -- converted during upgrade to edgy
UUID=89bceb88-65e2-4c7b-bd47-99aef27982b3 swap swap defaults 0 0



```

---

### Post by wgscott on 2006-12-01
While cleaning up the mess, I noticed the root partition on the main drive had this added:

errors=remount-ro

The disks that had this behaved as though that was issued (but didn't).  Is this the new default behavior?  If so, it is insane.

---

### Post by wgscott on 2006-12-01
Now everything, including the root partition, is read-only.

](*,)

---

### Post by wgscott on 2006-12-06
I cleaned up my /etc/fstab, picked a new mount point for my slave drives, and everything went well for about 48 hours.


I have now noticed that the appearance of this problem might be coincident with the XFCE screensaver coming on.

---

### Post by wgscott on 2006-12-12
I finally gave up, reformatted the root partition, and then did a clean install of 6.06 and subsequently used apt to upgrade to 6.10.  So far (1.5 days into Edgy) and the problem has not reoccurred.  I am cautiously optimistic.

One thing of interest is that when I let ubuntu discover the slave drive hardware, it mounts both disks in /media and the entry in /etc/fstab uses a different syntax than what I had when I did this manually (mounting first at /mnt and then at root level).

---

### Post by wgscott on 2006-12-12
I spoke too soon.  The problem persists even after a clean install of 6.06 and upgrade to 6.10.

Guess I will have to revert to 6.06.

---

