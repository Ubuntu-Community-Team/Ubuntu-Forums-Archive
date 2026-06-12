---
title: "trying to mount an NTFS Raid 0 partition"
date: 2007-10-15
forum: General Help
---

### Post by Stuart_1745 on 2007-10-15
ok I just moved my desktop over to Ubuntu from windows xp.  now in windows I had 2 drives a 1210gb main drive and a 500gp media drive(this is the raid 0 array made with 2 250gb drives) I wiped out the 120gb for the root partition of Ubuntu. and now Im trying to get access to my media files that are on the raid array.

ok here is the output from fdisk -l
```

Disk /dev/sda: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x65b65288

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1       60802   488392033+   7  HPFS/NTFS

Disk /dev/sdb: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x00000000

Disk /dev/sdb doesn't contain a valid partition table

Disk /dev/hdb: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x93bca89a

   Device Boot      Start         End      Blocks   Id  System
/dev/hdb1   *           1       13995   112414806   83  Linux
/dev/hdb2           13996       14593     4803435    5  Extended
/dev/hdb5           13996       14593     4803403+  82  Linux swap / Solaris

```

now I made a directory at /mnt/media to mount the /dev/sda1 drive to 

but when I do a  mount -t ntfs /dev/sda1 /mnt/media
I get this
```

 NTFS signature is missing.
Failed to mount '/dev/sda1': Invalid argument
The device '/dev/sda1' doesn't have a valid NTFS.
Maybe you selected the wrong device? Or the whole disk instead of a
partition (e.g. /dev/hda, not /dev/hda1)? Or the other way around?

```

I also when I open it with gpartition it shows that I have 2 250 gb drives but they both dont have any partition on them

btw the sata controller I am using is a ULI 5289

now is this a problem with my raid controller not being "fully" hardware raid( I thought it was but Im starting to doubt that)? or is it something else

any help would be greatly appreciated

---

### Post by Pumalite on 2007-10-15
[https://help.ubuntu.com/community/FakeRaidHowto](https://help.ubuntu.com/community/FakeRaidHowto)

---

### Post by Stuart_1745 on 2007-10-15
ok dmraid -ay said no it has no raid drives 

so following the directions here is the output file and the output of the fdisk
```

Disk /dev/sda: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders, total 488397168 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x65b65288

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1              63   976784129   488392033+   7  HPFS/NTFS

```
[http://www.pearcerobotics.com/stuart/outputfile.tar.gz]("http://www.pearcerobotics.com/stuart/outputfile.tar.gz")

again thans for the help

---

### Post by Stuart_1745 on 2007-10-15
well Ive found out that ULI isnt suported by DMraid. they have ULI drivers for linux but its for fedora 3 redhat 9 and suse9.

so what should I do now?

---

### Post by Pumalite on 2007-10-15
Get rid of the Raid Array. I did. Raid0=Minimal improvement; Raid 5= Running around with suspenders and a belt and nothing to show for it. Unless you have a hardware Raid, don't bother with it.

---

### Post by Stuart_1745 on 2007-10-15
yeah thats what I plan on doing with it  . . but untill then i have about 240+ gb of data on it that I would like to keep(documents, a windows back up, several multimedia files)

---

### Post by Pumalite on 2007-10-15
TrueImage it and pack it in an external hard drive. Later you can restore it to one of the hard drives if you want.

---

### Post by Stuart_1745 on 2007-10-15
ok I think that will work.


again thanks for the help

ok and for all the people like me who spend days looking on the internet let me sum up.
this applied for my NTFS raid 0 partition

if you have a ULI raid array   you have what is known as a fake raid(not fully software but not fully hardware either)

the tool that you would use for normally accessing one of these arrays is called dmraid . . and it does not support ULI chip sets. Uli also does not have drivers for any current linux distro( ubuntu, fc7,RHwhatever#theyareat)

so do what Pumalite told me. back it up to a n external HD then reformat it and reload it.
end sum up

and thanks again for the help

---

### Post by Pumalite on 2007-10-15
Happy Ubuntuing!

---

