---
title: "Fix my fstab"
date: 2007-09-04
forum: General Help
---

### Post by iitywygms on 2007-09-04
I have been messing with this for the last two days and cant get it right.  I have a volume on my desktop that will not unmount.  I have read and read but cant get it right.  Here is the information I have,

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda5
UUID=af8e57a1-fba5-4356-a2ea-5f570780faae
defaults,errors=remount-ro 0       1                      swap
# /dev/sda2
UUID=49ed2e26-49f5-4772-886b-526a200ed402 /               ext3    defaults,errors=remount-ro 0       1
# /dev/sdb1
UUID=B0E0BDD8E0BDA54E /media/sdb1     ntfs    defaults,nls=utf8,umask=007,gid=46 0       1           
# /dev/sdb5
UUID=af8e57a1-fba5-4356-a2ea-5f570780faae none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/scd1       /media/cdrom1   udf,iso9660 user,noauto     0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto  0       0


fdisk -l


Disk /dev/sda: 40.0 GB, 40020664320 bytes
255 heads, 63 sectors/track, 4865 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1            4661        4865     1646662+   5  Extended
/dev/sda2               1        4660    37431416   83  Linux
/dev/sda5            4661        4865     1646631   82  Linux swap / Solaris

Partition table entries are not in disk order

Disk /dev/sdb: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1        5099    40957686    7  HPFS/NTFS
/dev/sdb2            5100        9729    37190475    5  Extended
/dev/sdb5            5100        9729    37190443+  83  Linux




 ls -l /dev/disk/by-uuid
total 0
lrwxrwxrwx 1 root root 10 2007-09-04 13:01 49ed2e26-49f5-4772-886b-526a200ed402 -> ../../sda2
lrwxrwxrwx 1 root root 10 2007-09-04 13:01 a8af048e-8243-403e-8493-dc6cba59d5db -> ../../sdb5
lrwxrwxrwx 1 root root 10 2007-09-04 13:01 af8e57a1-fba5-4356-a2ea-5f570780faae -> ../../sda5
lrwxrwxrwx 1 root root 10 2007-09-04 13:01 B0E0BDD8E0BDA54E -> ../../sdb1
kevin@ubuntu:~$ 


I know i know I should figure this out myself but I am goin nuts here.

Thanks

---

### Post by merlinus on 2007-09-04
From what I can see, sdb5 is a linux partition, not a swap partition.

Also, the partition numbers on sda seem mixed up.

-merlin

---

### Post by iitywygms on 2007-09-04
I probably have everything hosed right not.  If one of you experts could do some editing it would be much appreciated.

thanks again

---

### Post by meierfra on 2007-09-04
Could you tell us what you want to unmount? Is it the windows partition? 

Then you need to put a #  in front  of the corresponding line of the fstab:

```
# UUID=B0E0BDD8E0BDA54E /media/sdb1 ntfs defaults,nls=utf8,umask=007,gid=46 0 1 
```

---

### Post by iitywygms on 2007-09-04
When I right click on the volume that is on my desktop, sdb1, and click unmount volume I get this error
umount: :/media/sdb1 mount disagrees with the fstab.

It is my widows volume.
I can comment it out in fstab, and it will go away.  But I just want to make everything right.

I get mounting errors when booting up also.  Cant give alot of details because it disappears to quick.

Thanks

---

### Post by merlinus on 2007-09-04
gid=46 seems incorrect, if both the owner and group are root, according to   ls -l /dev/disk/by-uuid.

-merlin

---

### Post by iitywygms on 2007-09-04
> **merlinus said:**
> gid=46 seems incorrect, if both the owner and group are root, according to   ls -l /dev/disk/by-uuid.

-merlin

HUH?

---

### Post by merlinus on 2007-09-04
Try deleting gid=46 from this line:

UUID=B0E0BDD8E0BDA54E /media/sdb1 ntfs defaults,nls=utf8,umask=007,gid=46 0 1

-merlin

---

### Post by iitywygms on 2007-09-05
Okay I removed what you suggested.  My windows volume no longer shows up on desktop or in computer. It is no longer visible anywhere. Close but no cigar

I also caught the boot up errors
1. mount point does not exist
2. mount point 0 does not exist.

Any other suggestions?
I really appreciate the help. Thanks

---

### Post by meierfra on 2007-09-05
I can tell you how to fix your fstab. But I need to know exactly what you want. 

Your last message sounds like that you want windows to appear in "computer" but not on your desktop. Is that right?

Also currently  your second linux partition (sdb5)  is not mounted  at boot up. Is that how you want it?

---

### Post by iitywygms on 2007-09-05
> **meierfra said:**
> I can tell you how to fix your fstab. But I need to know exactly what you want. 

Your last message sounds like that you want windows to appear in "computer" but not on your desktop. Is that right?

Also currently  your second linux partition (sdb5)  is not mounted  at boot up. Is that how you want it?

Yes, I want windows to appear in computer but not on desktop.  I know how to disable that using gconf-editor. By the way, i have gconf-editor set to _not show_ mounted drives _but my windows drive did_, until i removed gid=46  Now windows does not show up anywhere.

I would like sdb5 to be mounted at bootup.

thanks

---

### Post by logos34 on 2007-09-05
> **iitywygms said:**
> Yes, I want windows to appear in computer but not on desktop.  I know how to disable that using gconf-editor. By the way, i have gconf-editor set to _not show_ mounted drives _but my windows drive did_, until i removed gid=46  Now windows does not show up anywhere.

I would like sdb5 to be mounted at bootup.

thanks

Try this:
> 
# /etc/fstab: static file system information.
#
# <file system> <mount point> <type> <options> <dump> <pass>
proc /proc proc defaults 0 0
# /dev/sd**[COLOR="Red"]b[/COLOR]**5
UUID=**[COLOR="Red"]a8af048e-8243-403e-8493-dc6cba59d5db[/COLOR]**
defaults,errors=remount-ro 0 **[COLOR="Red"]2[/COLOR]**
# /dev/sda2
UUID=49ed2e26-49f5-4772-886b-526a200ed402 / ext3 defaults,errors=remount-ro 0 1
# /dev/sdb1
UUID=B0E0BDD8E0BDA54E /media/sdb1 ntfs defaults,nls=utf8,umask=007,gid=46 0 1
# /dev/sd**[COLOR="Red"]a[/COLOR]**5
UUID=af8e57a1-fba5-4356-a2ea-5f570780faae none swap sw 0 0
/dev/scd0 /media/cdrom0 udf,iso9660 user,noauto 0 0
/dev/scd1 /media/cdrom1 udf,iso9660 user,noauto 0 0
/dev/fd0 /media/floppy0 auto rw,user,noauto 0 0

---

### Post by iitywygms on 2007-09-05
I copy and pasted what you did into my fsab, rebooted. Still same error at boot up.
1. mount point does not exist
2. mount point 0 does not exist.

sdb1 now shows up on desktop. I can open it. It is the windblows volume.
I cannot unmount it, same error as before.

I now have a 35.5gb volume showing up in my computer but cannot open it.

here is the info again

fstab

 # /etc/fstab: static file system information.
#
# <file system> <mount point> <type> <options> <dump> <pass>
proc /proc proc defaults 0 0
# /dev/sdb5
UUID=a8af048e-8243-403e-8493-dc6cba59d5db
defaults,errors=remount-ro 0 2
# /dev/sda2
UUID=49ed2e26-49f5-4772-886b-526a200ed402 / ext3 defaults,errors=remount-ro 0 1
# /dev/sdb1
UUID=B0E0BDD8E0BDA54E /media/sdb1 ntfs defaults,nls=utf8,umask=007,gid=46 0 1
# /dev/sda5
UUID=af8e57a1-fba5-4356-a2ea-5f570780faae none swap sw 0 0
/dev/scd0 /media/cdrom0 udf,iso9660 user,noauto 0 0
/dev/scd1 /media/cdrom1 udf,iso9660 user,noauto 0 0
/dev/fd0 /media/floppy0 auto rw,user,noauto 0 0


fdisk -l

Disk /dev/sda: 40.0 GB, 40020664320 bytes
255 heads, 63 sectors/track, 4865 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1            4661        4865     1646662+   5  Extended
/dev/sda2               1        4660    37431416   83  Linux
/dev/sda5            4661        4865     1646631   82  Linux swap / Solaris

Partition table entries are not in disk order

Disk /dev/sdb: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1        5099    40957686    7  HPFS/NTFS
/dev/sdb2            5100        9729    37190475    5  Extended
/dev/sdb5            5100        9729    37190443+  83  Linux


blkid

/dev/sda5: TYPE="swap" UUID="af8e57a1-fba5-4356-a2ea-5f570780faae" 
/dev/sdb1: TYPE="ntfs" 
/dev/sdb2: TYPE="ntfs" 
/dev/sda2: UUID="49ed2e26-49f5-4772-886b-526a200ed402" SEC_TYPE="ext2" TYPE="ext3" 
/dev/sdb5: UUID="a8af048e-8243-403e-8493-dc6cba59d5db" SEC_TYPE="ext2" TYPE="ext3" 


 ls -l /dev/disk/by-uuid

total 0
lrwxrwxrwx 1 root root 10 2007-09-04 16:00 49ed2e26-49f5-4772-886b-526a200ed402 -> ../../sda2
lrwxrwxrwx 1 root root 10 2007-09-04 16:00 a8af048e-8243-403e-8493-dc6cba59d5db -> ../../sdb5
lrwxrwxrwx 1 root root 10 2007-09-04 16:00 af8e57a1-fba5-4356-a2ea-5f570780faae -> ../../sda5
lrwxrwxrwx 1 root root 10 2007-09-04 16:00 B0E0BDD8E0BDA54E -> ../../sdb1

thanks again

---

### Post by merlinus on 2007-09-05
sdb5 has no mountpoint specified in /etc/fstab.  According to blkid, it is formatted as ext3.

Info here:

[http://www.psychocats.net/ubuntu/mountlinux](http://www.psychocats.net/ubuntu/mountlinux)

-merlin

---

### Post by meierfra on 2007-09-05
Do the  directories /media/sdb1 and /media/sdb5 exist?  If not create them via:

```
sudo mkdir /media/sdb1
```
```
sudo mkdir /media/sdb5
```

---

### Post by logos34 on 2007-09-05
oops, no mountpoint! . I knew I'd leave out something.  

Do like meiefra and merlinus suggest above.

entry should be:

> # /dev/sdb5
UUID=a8af048e-8243-403e-8493-dc6cba59d5db **/media/sdb5 ext3** defaults,errors=remount-ro 0 2

sorry about that!

---

### Post by iitywygms on 2007-09-05
Thanks everyone. I will give it a go later tonight.

---

### Post by iitywygms on 2007-09-05
I did as suggested in above 3 post.

I had to make directory for sdb5, sdb1 already existed.

sdb1 and sdb5 show up on desktop.

i can click on either one and the contents are displayed.


I cannot unmount either one. same error as before.

Any other suggestions?

Thnaks

---

### Post by iitywygms on 2007-09-05
during boot up i get the error
bad format on line 1 of /etc/fstab

---

### Post by merlinus on 2007-09-05
You might post your current /etc/fstab.

Also, unmounting usually has to be done as root.

-merlin

---

### Post by meierfra on 2007-09-05
> I know how to disable that using gconf-editor. By the way, i have gconf-editor set to not show mounted drives 

This really should prevent   volumes from appearing on the desktop.

Maybe you could double check: Open gconf-editor,  go to apps-> nautilus -> desktop and see whether "volumes_visible" is still unchecked.

Are your using any other desktop managers?  I for example have ubuntu-desktop, xubuntu-desktop and kubuntu-desktop installed.  And sometimes changing a setting   in  say   a kde (=kubuntu) session,   screws up my settings for  gnome (=ubuntu) sessions.

---

### Post by meierfra on 2007-09-05
Just another thought: Is sdb an external drive? If yes you might play with the setting in 

System-> Preferences->Removable Drives and Media

---

### Post by iitywygms on 2007-09-05
I am only using gnome.  They are not external drives.
Show volumes is not checked in gconf-editor but the volumes still show on desktop.  I still cannot unmount them.

I fixed the bootup errors that I was having.

I have had some bootup messages that may give some information.  I am not sure if they are normal or not.

[2.951207] usb1-1 device not accepting address 2, error 71
kinit name_to_dev_t (/dev/sda5) = sda5 (8,5)
kinit trying to resume from /dev/sda5
kinit no resume image, doing normal boot

all says ok after that

fstab

# /etc/fstab: static file system information.
# <file system> <mount point> <type> <options> <dump> <pass>
proc /proc proc defaults 0 0
# /dev/sdb5
UUID=a8af048e-8243-403e-8493-dc6cba59d5db /media/sdb5 ext3 defaults,errors=remount-ro 0 2
# /dev/sda2
UUID=49ed2e26-49f5-4772-886b-526a200ed402 / ext3 defaults,errors=remount-ro 0 1
# /dev/sdb1
UUID=B0E0BDD8E0BDA54E /media/sdb1 ntfs defaults,nls=utf8,umask=007,gid=46 0 1
# /dev/sda5
UUID=af8e57a1-fba5-4356-a2ea-5f570780faae none swap sw 0 0
/dev/scd0 /media/cdrom0 udf,iso9660 user,noauto 0 0
/dev/scd1 /media/cdrom1 udf,iso9660 user,noauto 0 0
/dev/fd0 /media/floppy0 auto rw,user,noauto 0 0


fdisk -l

Disk /dev/sda: 40.0 GB, 40020664320 bytes
255 heads, 63 sectors/track, 4865 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1            4661        4865     1646662+   5  Extended
/dev/sda2               1        4660    37431416   83  Linux
/dev/sda5            4661        4865     1646631   82  Linux swap / Solaris

Partition table entries are not in disk order

Disk /dev/sdb: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1        5099    40957686    7  HPFS/NTFS
/dev/sdb2            5100        9729    37190475    5  Extended
/dev/sdb5            5100        9729    37190443+  83  Linux


 ls -l /dev/disk/by-uuid

lrwxrwxrwx 1 root root 10 2007-09-05 10:08 49ed2e26-49f5-4772-886b-526a200ed402 -> ../../sda2
lrwxrwxrwx 1 root root 10 2007-09-05 10:08 a8af048e-8243-403e-8493-dc6cba59d5db -> ../../sdb5
lrwxrwxrwx 1 root root 10 2007-09-05 10:08 af8e57a1-fba5-4356-a2ea-5f570780faae -> ../../sda5
lrwxrwxrwx 1 root root 10 2007-09-05 10:08 B0E0BDD8E0BDA54E -> ../../sdb1

blkid

/dev/sda5: UUID="af8e57a1-fba5-4356-a2ea-5f570780faae" TYPE="swap" 
/dev/sdb1: TYPE="ntfs" 
/dev/sdb2: TYPE="ntfs" 
/dev/sda2: UUID="49ed2e26-49f5-4772-886b-526a200ed402" SEC_TYPE="ext2" TYPE="ext3" 
/dev/sdb5: UUID="a8af048e-8243-403e-8493-dc6cba59d5db" SEC_TYPE="ext2" TYPE="ext3" 


thank you everyone

---

### Post by iitywygms on 2007-09-05
One other thing.  If I do a update grub and save it, it will not boot.  I have to edit grub menu.lst and change (0,0) to (0,1)

Dont know if that gives any clues.

---

### Post by merlinus on 2007-09-05
As I said in a post near the beginning of this thread, if you look at the results of sudo fdisk -l, you will see that your sda partitions are misnumbered, in terms of where they are located on the hdd.

The first on the disk physically is sda2, and therefore should be numbered sda1.  But sda1 is your extended partition, which is actually second, and should be numbered sda2.

This would seem to be the source of at least several of your problems, including the one with reinstalling grub.

-merlin

---

### Post by iitywygms on 2007-09-06
I see what you see. Not to sound dumb but how do I re-number them.  All I see in fstab is sdb5, sda2, sdb1 and sda5

should I change sda2 to sda1 in fstab?

thanks for your patience.  I have learned alot thru these forums but this one is buggin my brain.

---

### Post by merlinus on 2007-09-06
Changing partition numbers in /etc/fstab will not change them on your hdd.

What does this show:

```

df -h

```

-merlin

---

### Post by iitywygms on 2007-09-06
df -h
Filesystem            Size  Used Avail Use% Mounted on
/dev/sda2              36G  7.4G   27G  22% /
varrun                379M   64K  379M   1% /var/run
varlock               379M     0  379M   0% /var/lock
procbususb            379M  116K  379M   1% /proc/bus/usb
udev                  379M  116K  379M   1% /dev
devshm                379M     0  379M   0% /dev/shm
lrm                   379M   33M  346M   9% /lib/modules/2.6.20-16-generic/volatile
/dev/sdb5              35G  177M   33G   1% /media/sdb5
/dev/sdb1              40G   26G   14G  65% /media/sdb1

---

### Post by meierfra on 2007-09-06
Try this:

add "users" to the options in the fstab:

> 
UUID=a8af048e-8243-403e-8493-dc6cba59d5db /media/sdb5 ext3 defaults,[COLOR="Red"]users,[/COLOR]errors=remount-ro 0 2
 and

> 
UUID=B0E0BDD8E0BDA54E /media/sdb1 ntfs defaults,[COLOR="Red"]users,[/COLOR]nls=utf8,umask=007,gid=46 0 1

This should allow you to unmount the two partitions and remount them in "Computer" ( But they still appear on the desktop anytime they are mounted.) You don't need to reboot for these changes to take effect.

If you don't want the partition to be mounted at boot up,  you need to add "noauto" to the options. But  since "auto" is one of the default options, you might have to remove "default".   "man mount"   contains lost of information on mounting, for example it lists all the "default" options.

---

### Post by iitywygms on 2007-09-06
No joy.

current fstab

# /etc/fstab: static file system information.
# <file system> <mount point> <type> <options> <dump> <pass>
proc /proc proc defaults 0 0
# /dev/sdb5
UUID=a8af048e-8243-403e-8493-dc6cba59d5db /media/sdb5 ext3 defaults,users,errors=remount-ro 0 2
# /dev/sda1
UUID=49ed2e26-49f5-4772-886b-526a200ed402 / ext3 defaults,errors=remount-ro 0 1
# /dev/sdb1
UUID=B0E0BDD8E0BDA54E /media/sdb1 ntfs defaults,users,nls=utf8,umask=007,gid=46 0 1
# /dev/sda5
UUID=af8e57a1-fba5-4356-a2ea-5f570780faae none swap sw 0 0
/dev/scd0 /media/cdrom0 udf,iso9660 user,noauto 0 0
/dev/scd1 /media/cdrom1 udf,iso9660 user,noauto 0 0
/dev/fd0 /media/floppy0 auto rw,user,noauto 0 0

---

### Post by meierfra on 2007-09-06
Do

```
sudo umount /media/sdb1
```

And then see whether you can mount sdb1 in Computers.

---

### Post by iitywygms on 2007-09-06
I run that and I can still mount the drive in computers.

---

### Post by meierfra on 2007-09-06
Can you unmount it on the desktop?

---

### Post by iitywygms on 2007-09-06
> **meierfra said:**
> Can you unmount it on the desktop?

Nope

---

### Post by iitywygms on 2007-09-06
If i sudo umount/media/sdb1 or sdb5 they disappear from the desktop.  They are still visible in computer.  If I click on them in my computer they reappear on the desktop. If I right click on the desktop and select unmount, i get the mount disagrees with fstab error.  
What is really strange is that nautilus will not affect anything, if I choose to have the trash can visible or home folder visible they do not show up.  Is Nautilus screwed up or something else?
I am buggin!

---

### Post by meierfra on 2007-09-06
O..K.  I give up. I had tested the "users" thing on my computer and it worked perfectly.  There is just a tiny change that it works after rebooting, but not worth rebooting now.


As far as I know your screwed up partition order shouldn't  course any real  problems.  I googled  and it seems one can change the order using "fdisk" on the commandline, but I know nothing about that.

---

### Post by meierfra on 2007-09-06
Ignore

---

### Post by iitywygms on 2007-09-06
> **meierfra said:**
> Ignore

Am I missing something?

---

### Post by meierfra on 2007-09-06
> Am I missing something?

Oops, that "ignore" was misleading. I had misread your previous post and posted some nonsense. So I deleted it and replaced it by "ignore" as in "ignore this message"


But I  just reproduced your "mount disagrees with the fstab" message on my computer and I might be able to fix it . 


Replace the UUID by the device name:

> /[COLOR="Red"]dev/sdb5 [/COLOR] /media/sdb5 ext3 defaults,users,errors=remount-ro 0 2


/[COLOR="Red"]dev/sdb1 [/COLOR] /media/sdb1 ntfs defaults,users,nls=utf8,umask=007,gid=46 0 1

---

### Post by iitywygms on 2007-09-06
meierfra  YOU ROCK!!!!


All is well.  If you are ever in the 707 area of cali give me a shout and I will buy you a cold beer.

I can sleep now

---

### Post by iitywygms on 2007-09-06
Thanks to everyone else also.  

This forum and everyone in it is the best by far..................

---

### Post by meierfra on 2007-09-06
> I can sleep now
Me  too.

Anybody out there  who knows why replacing  the UUID by the name makes a difference?

I just googled  the error message (mount disagrees with the fstab) and found somebody else solving the problems in this way.
Then I tried it on my computer, and sure enough using UUID's   I  got the same error message.

---

### Post by logos34 on 2007-09-06
> **meierfra said:**
> 
Anybody out where  who knows why replacing  the UUID by the name makes a difference?

Nice work Meierfra and Merlinus!  So it was the damn UUID! And this despite the fact that it matches the ls -l /dev/disk/by-uuid output.    

I wish I knew the answer to your question, because I've been wondering about uuids lately.  I'm slowly coming to the conclusion that UUID's cause more trouble than they're worth.  I think in the future at the first sign of trouble I'll just just cut to the chase and recommend that people take them out.  AFAIK there's really no need for them unless you work with portable external drives (flash, usb hard disks) or you're running a server with removable rackmount drives.  As I've said before, I don't like them and I've eliminated them in my fstab on partitions that I work with a lot (i.e. reformat and install to, as well as swap).  

I wonder if a stripped down entry with no uuid and just 'defaults' is not the best for your average (non-root) ext3 partition.  I have a couple of lines like that.  Not fancy but it works hassle free--no more worrying about changing uuids after a reformat, while ''defaults' is fine for the average single user. 

Just some thoughts on my mind.

---

### Post by merlinus on 2007-09-06
Just shows how everyone hanging in there with the process can often bring a situation to a successful conclusion.

I do not like UUIDs for another reason.  If you resize or move a partition, even if you restore it to the original size soon after, its UUID will change, and perhaps the others around it as well.  Then ubuntu will not load.

As for defaults, I use uid and gid for my ntfs partitions so I am the owner with full permissions.

Good work!

-merlin

---

