---
title: "10 GB Volume"
date: 2008-05-15
forum: General Help
---

### Post by hidarikani on 2008-05-15
I had an NTFS partition. Then I downloaded Gparted and formatted it to ext3.
Now when I'm trying to access it through Nautilus I get this msg:

Access to this internal disc is restricted to system administrators only for security reasons. Please enter your password to proceed.

Of course I can enter my pw and the volume will get mounted, but I can't save files to it: Permission denied.

So how can I change partition permissions?

---

### Post by housam on 2008-05-15
right click on the disk >> properties >> permissions >> change the settings for folders and files to read & write.

---

### Post by hidarikani on 2008-05-21
I changed the permissions for /media/sda2/ which is my new ext3 partition. Now I can read&write to it without sudo.

However Nautilus says it has only 4 GB of free space. It's supposed to be 10 GB because 10 is what I see in GParted. Then in the Nautilus sidebar I see a '10 GB volume' I click it and an 'enter you password' window appears. So I enter my pw an wualla I get a 'disk' mounted with 10 gigs of free space.

Could someone please tell me what the hell is going on? :)

---

### Post by danwood76 on 2008-05-21
I think you may have issues in your fstab.
Can you post it please:
```

cat /etc/fstab

```

---

### Post by hidarikani on 2008-05-21
Hmm interesting /media/sda2 shows up in GParted as ext3, but it's  ntfs in fstab. How do I update my fstab?

```

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda4
UUID=26117aac-507f-4e57-b0f2-b28aff8c073f /               ext3    defaults,errors=remount-ro 0       1
# /dev/sda1
UUID=ECCC929DCC92619E /media/sda1     ntfs    defaults,umask=007,gid=46 0       1
# /dev/sda2
UUID=446863186863084E /media/sda2     ntfs    defaults,umask=007,gid=46 0       1
# /dev/sda5
UUID=0408856F08856112 /media/sda5     ntfs    defaults,umask=007,gid=46 0       1
# /dev/sda6
UUID=ce0d54b7-b83c-46fe-adf7-ab052360c3ac none            swap    sw              0       0
/dev/hda        /media/cdrom0   udf,iso9660 user,noauto,exec 0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec 0       0
usbfs /proc/bus/usb usbfs auto 0 0


```

---

### Post by hidarikani on 2008-05-21
It looks like fstab is created during the installation of the OS and doesn't change afterwards. So if I add a new hdd or reformat smth the changes won't be merged into it.

Am I right?

---

### Post by hidarikani on 2008-05-21
bounce

---

### Post by danwood76 on 2008-05-21
It will be that errornous fstab line thats causing issues I bet.

open up fstab for editing:
```

sudo gedit /etc/fstab

```
then change th sda2 line to be:
```

UUID=446863186863084E /media/sda2     ext3    defaults 0       1

```
Note I also removed the permissions, I dont see much issue with this unless you run a multi user system then replace them, it just gives less chance of problems this way.

ANd yes if you add a new drive and so on its necessary to update the fstab. (if you want it to automount)
I assume there must be some GUI for setting this up (and if not why not?) but I like just text editing it personally.

---

### Post by hidarikani on 2008-05-22
The solution you've posted almost worked.
Then I've found this
> If you re-format the partition the UUID will change
and
> To list the partitions by UUID : blkid
So I updated my UUID and everything works fine now.

Thanx

---

