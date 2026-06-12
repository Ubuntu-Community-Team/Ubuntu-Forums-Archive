---
title: "Mounting Partitions"
date: 2007-02-17
forum: General Help
---

### Post by Sterkarm on 2007-02-17
high - i curently have two partions  - both ext3

im using the second one (hda2) with ubuntu, but id like to be abel to mount the other partitions as well in order to be abel to read / write to it.

PLZ help witht telling me how to do this, and please take me though this stedaly so i can understand 

thanx

---

### Post by taurus on 2007-02-17
Paste the output of these two commands from a terminal here.

```
id
sudo fdisk -l
```

---

### Post by Sterkarm on 2007-02-17
thease r the replies i got: 

id 

uid=1000(matt) gid=1000(matt) 
groups=0(root),4(adm),20(dialout),21(fax),24(cdrom),25(floppy),26(tape),29(audio),30(dip),44(video),46(plugdev),106(lpadmin),110(scanner),112(admin),1000(matt)

sudo fdisk -l 

Disk /dev/hda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1               1        5099    40957686   83  Linux
/dev/hda2            5100        9565    35873145   83  Linux
/dev/hda3            9566        9729     1317330    5  Extended
/dev/hda5            9566        9729     1317298+  82  Linux swap / Solaris

Disk /dev/sda: 2049 MB, 2049900032 bytes
129 heads, 31 sectors/track, 1001 cylinders
Units = cylinders of 3999 * 512 = 2047488 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1        1002     2001840    e  W95 FAT16 (LBA)
Partition 1 has different physical/logical endings:
     phys=(1007, 128, 31) logical=(1001, 22, 30)

---

### Post by taurus on 2007-02-17
So, looks like you want to mount /dev/hda1 then.

```
gksudo gedit /etc/fstab
```
And add this line to the end of it.

```
/dev/hda1   /media/hda1   ext3   defaults   0   1
```
Save it.  Now, create a new mount point and mount it.

```
sudo mkdir /media/hda1
sudo mount -a
```
And since you want to be able to write to it, you need to change the ownership of /media/hda1.

```
sudo chown -R matt:matt /media/hda1
```

---

### Post by Sterkarm on 2007-02-17
hmm, i folw most of what youv said theri - but what do you mean by creat a new mount point and mount it ? 

sorry im not realy that good at this stuff - 

foolwed the coding though - but dosent seam to have done anything ?

---

### Post by Sterkarm on 2007-02-17
ah, scratch that - wprked out what you toldme to do - i do have a brain after all :P 


thanx loads dude

---

