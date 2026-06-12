---
title: "Configuring fstab to give ntfs read/write acces."
date: 2013-06-07
forum: General Help
---

### Post by Crypdos on 2013-06-07
Hello, 

This problem is driving me crazy  ... I've been googling for hours now, trying a lot of stuff - but nothing has worked yet.

I just can't obtain write rights for my NTFS HDD. 

my fstab:
```
# /etc/fstab: static file system information.
#
# Use 'blkid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda2 during installation
UUID=5a1e8c36-abdd-496a-8421-e6486df36fc7 /               ext4    noatime,discard,errors=remount-ro 0       1
# /home was on /dev/sda3 during installation
UUID=088cb6f0-84f9-4246-98ae-5d3662d2d8ec /home           ext4    noatime,discard,defaults        0       2
# swap was on /dev/sda1 during installation
UUID=15dad974-4171-4753-bd9c-f6610589368f none            swap    sw              0       0
# tmpfs
tmpfs   /tmp    tmpfs   defaults,noatime,mode=1777      0       0
#1,5TB HDD NTFS
UUID=3AB87D34B87CF02D /media/1,5TB ntfs-3g auto,uid=1000,gid=1000,dmask=027,fmask=137 0 0


```

I tried ntfs and ntfs-3g, it appears to make no difference. 

It could be that another program is conflicting with fstab, mounting it in a different way? I'm thinking this because when I remove the line in fstab, it still automounts (which shouldn't be the case without fstab right?). Unfortunately I don't know which program this could be, if there's any.

EDIT:
mount prints this:
```

/dev/sda3 on /home type ext4 (rw,noatime,discard)
/dev/sdb1 on /media/1,5TB type fuseblk (rw,nosuid,nodev,allow_other,default_permissions,blksize=4096)

```
It's being mounted with different options then specified in fstab, right?

Thanks in advance.

---

### Post by ajgreeny on 2013-06-07
I think the normal fstab entry for ntfs, assuming you have ntfs-3g installed, is either
```
UUID=66E53AEC54455DB2 /media/storage/    ntfs-3g        auto,user,rw 0 0
```or, according to more recent info I have
```
UUID=66E53AEC54455DB2 /media/storage  ntfs    defaults    0    0
```Change the UUIDs to fit, of course.
If that does not help, I don't know if this is anything to do with it, so forgive me if I send you on a wild-goose-chase, but I am wondering if your label for the partition on the disk, which I assume you have as **1,5TB** is causing a problem simply because it has a comma **,** in it.

I may be completely wrong, but maybe just changing the label to something else may help.  Worth a try?

---

### Post by Crypdos on 2013-06-07
Hello,

I tried this
```

#1,5TB HDD NTFS
#UUID=3AB87D34B87CF02D /media/1,5TB ntfs-3g auto,uid=1000,gid=1000,dmask=027,fmask=137 0 0
UUID=3AB87D34B87CF02D /media/1,5TB ntfs defaults 0 0

```

It worked and I was about to thank you, but after I rebooted again it didn't work. Tried rebooting 5 times, didn't work a single time :(.
I believe I had this already, that it worked randomly for 1 boot. But I couldn't reproduce it.

I don't know how I can change the label in ubuntu. I set this in Windows a while ago.

---

### Post by oldfred on 2013-06-07
I use Disk Utilitiy (or Disks?) to change labels. But not for anything partition related. You can also use gparted or command line to change labels.

Another suggestion on NTFS settings. I also wonder about , in mount. You have to define your mount first, where system automounting uses label or defaults to size or UUID.

       [http://ubuntuforums.org/showthread.php?t=1983336](http://ubuntuforums.org/showthread.php?t=1983336)
Mount & edit fstab from Morbius1 - suggest using templates instead. Post #6
For ntfs UUID shown is example only see below:
UUID=DA9056C19056A3B3 /media/WinD ntfs defaults,nls=utf8,umask=000,uid=1000,windows_names 0 0
Window_names prevents the use of invalid windows characters:
(which are the nine characters &#8221; * / : < > ? \ | and those whose code is less than 0×20) 
uid=1000 should fix the trash problems as well:


 ** To find the correct UUID for your partitions:
sudo blkid -c /dev/null -o list
** You will have to create the mount point yourself, for example:
sudo mkdir /media/WinD

** Then add the template with the correct UUID and mount point to fstab:
sudo cp /etc/fstab /etc/fstab.backup
gksu gedit /etc/fstab

   ** And when you are done editing fstab and saving it run the following command to test for errors and mount the partitions without requiring a reboot. You will know before you reboot if something is amiss. Make sure you have partition unmounted if prevously mounted:
sudo mount -a

---

### Post by Crypdos on 2013-06-07
It works!

I made a new mountpoint
sudo mkdir /media/hdd1

Labeled the hdd as "mediahdd", and used the template from morbius1, my fstab:
UUID=3AB87D34B87CF02D /media/hdd1 ntfs defaults,nls=utf8,umask=000,uid=1000,windows_names 0 0

I'm glad it's working, thanks! But where did I go wrong? Was it just not creating a new mountpoint and using the old "1,5TB" label as a mountpoint (which wasn't a mountpoint?)

---

### Post by oldfred on 2013-06-07
Glad you got it working. :)

Not sure but I think it was the use of the auto mount label which was not really a mount point you could use. Someone else may know for sure.

---

