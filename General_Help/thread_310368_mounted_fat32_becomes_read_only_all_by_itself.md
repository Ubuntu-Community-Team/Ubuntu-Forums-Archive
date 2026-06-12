---
title: "mounted fat32 becomes read only all by itself"
date: 2006-12-01
forum: General Help
---

### Post by NiksaVel on 2006-12-01
I have a new strange problem which started happening since yesterday (the only change I did to the comp is uninstall beryl and xgl and started using metacity again)... I have read/write access to my mounted fat32 disk, but than after some time it becomes read only all by itself and I have to reboot to get access again...  somebody please help! :/


here is my fstab:

> # /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/hda3
UUID=5885ebeb-530f-4d5a-a125-0a3cebc8b57e /               ext3    defaults,errors=remount-ro 0       1
# /dev/hda6
UUID=2152d0c7-0bee-404a-9acf-d077a494351c none            swap    sw              0       0
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto     0       0
# /dev/hda5       /home/niksavel/windows/d  vfat iocharset=utf8,umask=000  0    0
/dev/hda5 /home/niksavel/windows/d vfat users,owner,rw,umask=000 0 0
/dev/hda1       /home/niksavel/windows/c   ntfs nls=utf8,umask=0222 0 0

---

### Post by CatKiller on 2006-12-01
> **NiksaVel said:**
> I have a new strange problem which started happening since yesterday (the only change I did to the comp is uninstall beryl and xgl and started using metacity again)... I have read/write access to my mounted fat32 disk, but than after some time it becomes read only all by itself and I have to reboot to get access again...  somebody please help! :/

Partitions get automatically remounted as read-only if there's been a problem with them to prevent anything else bad happening to them.

Perhaps your disk is no longer as reliable as it once was?

---

### Post by NiksaVel on 2006-12-01
well...  I most certainly hope not :)  it's my laptop and I don't even want to think about purchasing a 2.5" hdd..   


the computer is pretty reliable... I am dual booting ubuntu edgy and xp pro and both work solid..


I have never had a problem that might make me consider there might be something wring with the hdd...   and it's been working solid for 2 years now...    


dont't tell me that !!!   :mrgreen:

---

### Post by RaisedFist on 2006-12-01
I have the same problem. I have a HDD from my old laptop (which isn't really that old) and it wasn't used too much. I formated it in Edgy and then plugged it in with an USB adapter.
The system mounts it but in read-only state...

What could be the problem?

---

### Post by dbk927 on 2006-12-01
Try un-commenting the 10th line in /etc/fstab and comment the 11th line, so that it looks like:  

# /etc/fstab: static file system information.
#
# <file system> <mount point> <type> <options> <dump> <pass>
proc /proc proc defaults 0 0
# /dev/hda3
UUID=5885ebeb-530f-4d5a-a125-0a3cebc8b57e / ext3 defaults,errors=remount-ro 0 1
# /dev/hda6
UUID=2152d0c7-0bee-404a-9acf-d077a494351c none swap sw 0 0
/dev/hdc /media/cdrom0 udf,iso9660 user,noauto 0 0
/dev/hda5 /home/niksavel/windows/d vfat iocharset=utf8,umask=000 0 0
# /dev/hda5 /home/niksavel/windows/d vfat users,owner,rw,umask=000 0 0
/dev/hda1 /home/niksavel/windows/c ntfs nls=utf8,umask=0222 0 0

This same thing happened to me some time ago and that solved it.  Its like a second line for the fat partition (in this case hda5) just got automatically created, but the old one is in tact just commented, so switching it back seems to fix the problem.  I'm not sure what causes it, but this should help.

---

### Post by NiksaVel on 2006-12-01
heh... I just did that and it works fine for now, I'll see if it becomes read-only by itself during prolong period of work...

---

### Post by trixtah on 2006-12-07
I'm having a similar problem, in that my vfat partition has made itself interestingly read-only since the last round of edgy updates I applied today.

Here's the applicable line in /etc/fstab:
[B]
/dev/hda2    /media/fat32 vfat  iocharset=utf8,umask=000  0    0[/B]

It had a UUID after the Edgy migration, but I've left that out to simplify things for now. The partition was working perfectly up until that point!

(So much for my downloading the last eps of Heroes)

---

### Post by NiksaVel on 2006-12-07
I found that unmounting and remounting the partition returns it to read-write mode.

---

### Post by NiksaVel on 2006-12-07
oh yeah... and the second attempt did not change a thing... the partition is still rw at startup and at some point, for some reason becomes read only...   than I have to unmount and remount or reboot altogether...

---

### Post by trixtah on 2006-12-08
Well, unmounting and remounting doesn't help, so perhaps it's a different problem. Rebooting does not help either (done that a few times already)!

It's just stuck as read-only.

---

### Post by zanjabeel5 on 2008-02-02
I had the same problem as the original poster

found the solution here:
[http://www.linuxquestions.org/questions/linux-general-1/mounted-read-write-fat32-partition-suddenly-becomes-read-only-166190/](http://www.linuxquestions.org/questions/linux-general-1/mounted-read-write-fat32-partition-suddenly-becomes-read-only-166190/)

**The solution**

> I had the same problem but scandisk didn't fix it.
Here's what I did:
Log in as root
unmount the FAT filesystem -- umount /mnt/dos or wherever it's located.
/sbin/fsck.vfat -a /dev/hda5 or whichever device it is

This did a better job of fixing the bad clusters than scandisk.
You should get an output something like this:
Contains a free cluster (1). Assuming EOF.
Free cluster summary wrong (224825 vs. really 224826)
Auto-correcting.
Performing changes.
/dev/hda5: 786 files, 1693062/1917888 clusters

Then just remount the filesystem read-write and you're good to go.

and a worth reply 
> Just when you think you know a little bit about Linux, you find out it fixes MS fllesystems better too!.

Time to give a donation to the kernel team to encourage some neat NTFS stuff too!

---

