---
title: "USB drive wont work"
date: 2008-06-05
forum: General Help
---

### Post by rock4christ on 2008-06-05
when I try to use my usb drive(4gb Sandisk Cruiser Micro currently blank and formatted Fat32) I get this:
mount: wrong fs type, bad option, bad superblock on /dev/sdb1,
missing codepage or helper program, or other error
In some cases useful info is found in syslog - try
dmesg | tail or so

here is the result of dmesg | tail:
[ 1337.364661] sd 2:0:0:0: [sdb] Assuming drive cache: write through
[ 1337.367757] sd 2:0:0:0: [sdb] 8027790 512-byte hardware sectors (4110 MB)
[ 1337.368761] sd 2:0:0:0: [sdb] Write Protect is off
[ 1337.368767] sd 2:0:0:0: [sdb] Mode Sense: 03 00 00 00
[ 1337.368770] sd 2:0:0:0: [sdb] Assuming drive cache: write through
[ 1337.368778] sdb: sdb1
[ 1337.370243] sd 2:0:0:0: [sdb] Attached SCSI removable disk
[ 1337.370296] sd 2:0:0:0: Attached scsi generic sg2 type 0
[ 1338.304921] UDF-fs: No partition found (1)
[ 1338.439427] ISOFS: Unable to identify CD-ROM format.

what now?

---

### Post by ibuclaw on 2008-06-05
What is the output of the command
```
sudo blkid /dev/sdb1
```

Also, can you post your fstab file too.
```
cat /etc/fstab
```

Regards
Iain

---

### Post by rock4christ on 2008-06-05
for the first one there is absolutely nothing( just returns to corey@corey-laptop:~$)

for the second one I get this:

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda1
UUID=93f0ee8e-1cfa-4270-b84e-ccbb2a53fd5d /               ext3    relatime,errors=remount-ro 0       1
# /dev/sda5
UUID=9763a845-1388-4285-ab07-51209ec5354e none            swap    sw              0       0
/dev/sdb1       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/scd0       /media/cdrom1   udf,iso9660 user,noauto,exec,utf8 0       0



also, im not sure how to turn volume up or down is there a volume option somewhere, and/or a way to make my fn + page up/page down/end cause volume up/down/off respectively?

---

### Post by ibuclaw on 2008-06-05
I will try to answer your second question in a minute. But to stay on your first. (Less Confusion :) )
How many cdrom drives do you have?

[EDIT]
This will show me in plain text.
```
ls /dev/scd*
```
Regards
Iain

---

### Post by rock4christ on 2008-06-05
/dev/scd0

also. the cd drive doesn't work(not sure why, got the pc second hand for free) if that matters. I had to install via USB

---

### Post by ibuclaw on 2008-06-05
Ah, OK then.

That might explain everything then :)

Open your fstab file
```
gksu gedit /etc/fstab
```
And replace all the text with this.
```

# /etc/fstab: static file system information.
#
# <file system> <mount point> <type> <options> <dump> <pass>
proc /proc proc defaults 0 0
# /dev/sda1
UUID=93f0ee8e-1cfa-4270-b84e-ccbb2a53fd5d / ext3 relatime,errors=remount-ro 0 1
# /dev/sda5
UUID=9763a845-1388-4285-ab07-51209ec5354e none swap sw 0 0

/dev/scd0 /media/cdrom0 udf,iso9660 user,noauto,exec,utf8 0 0

```
The cdrom drive has been switched to mount in the right folder, and the erraneous fstab line has been removed.

Save the file, and type in:
```
sudo mount -a
```
And then reinsert your USB drive. It should mount alright now.

Regards
Iain

[EDIT]
Now, for your second question, what is the Manufacturer and Model of your Laptop?

---

### Post by rock4christ on 2008-06-05
im using a dell inspiron 5100

---

### Post by rock4christ on 2008-06-05
also, when I use youtube, I cant pause or change volume, and the loading circle stays in the center of the vid even while playing

---

### Post by rock4christ on 2008-06-05
I just noticed that youtube works fine when embeded on one of my favorite sites, so im confused

---

