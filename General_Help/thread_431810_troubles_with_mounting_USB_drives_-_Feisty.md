---
title: "troubles with mounting USB drives - Feisty"
date: 2007-05-03
forum: General Help
---

### Post by maso1870 on 2007-05-03
I've been scouring many places looking for a solution but have been unable to find any. 

My issue is that any USB key or digital camera memory is not mounting properly on Feisty Fawn. Let me explain what happens. If I have my computer open (showing all drives) and then plug in a key/insert memory into card reader the device quickly shows up but with a big red X in the top right of the icon then the device icon disappears. When I look at my Hardware Information the devices appear to be there. 

There have been a few times when they have actually mounted but it never seems to work when I want it to. It can't be an issue with the devices as they work on my laptop (also running Feisty). 

Any tips would be great!

Thanks,
Cole

---

### Post by taurus on 2007-05-03
With either one of the devices plugs in, post the output of this command from a terminal.

Applications -> Accessories -> Terminal
```
sudo fdisk -l
```

---

### Post by maso1870 on 2007-05-03
Thanks for the quick reply! Okay, with "sudo fdisk" -l this is returned:

[HTML]Disk /dev/sda: 251.0 GB, 251000193024 bytes
255 heads, 63 sectors/track, 30515 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       10199    81920000    7  HPFS/NTFS
/dev/sda2           13387       16573    25599577+   7  HPFS/NTFS
/dev/sda3           16574       29241   101749115    7  HPFS/NTFS
/dev/sda4           10200       13386    25599577+   5  Extended
/dev/sda5   *       10200       13248    24491061   83  Linux
/dev/sda6           13249       13386     1108453+  82  Linux swap / Solaris

Partition table entries are not in disk order

Disk /dev/sdb: 2055 MB, 2055021056 bytes
16 heads, 63 sectors/track, 3981 cylinders
Units = cylinders of 1008 * 512 = 516096 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1        3982     2006825    b  W95 FAT32[/HTML]

The device at the bottom is my 2GB USB key. When I attempt to mount it with "mount /dev/sdb1" this is returned:

[HTML]NTFS signature is missing.
Failed to startup volume: Invalid argument
Failed to mount '/dev/sdb1': Invalid argument
The device '/dev/sdb1' doesn't have a valid NTFS.
Maybe you selected the wrong device? Or the whole disk instead of a
partition (e.g. /dev/hda, not /dev/hda1)? Or the other way around?[/HTML]

This makes me think it wants it to be an NTFS drive.

---

### Post by taurus on 2007-05-03
Try

```
sudo mkdir /media/sdb1
sudo mount -t vfat /dev/sdb1 /media/sdb1 -o iocharset=utf8,umask=000
df -h
```

---

### Post by maso1870 on 2007-05-03
Okay, it won't allow me to make the directory because it says it already exists and upon performing the other actions this is what is returned:

```
Filesystem            Size  Used Avail Use% Mounted on
/dev/sda5              23G   13G  9.1G  59% /
varrun                506M  136K  506M   1% /var/run
varlock               506M     0  506M   0% /var/lock
procbususb            506M  176K  506M   1% /proc/bus/usb
udev                  506M  176K  506M   1% /dev
devshm                506M     0  506M   0% /dev/shm
lrm                   506M   33M  473M   7% /lib/modules/2.6.20-15-generic/volatile
/dev/sda1              79G   31G   48G  40% /media/sda1
/dev/sda2              25G  3.3G   22G  14% /media/sda2
/dev/sda3              98G   81G   17G  84% /media/sda3
/dev/hdb              672M  672M     0 100% /media/cdrom0
/dev/sdb1             2.0G  234M  1.7G  12% /media/sdb1
```

I had installed software previously to automatically mount NTFS drives. Is it possible this could have harmed mounting FAT/FAT32 devices?

Thanks again!

---

### Post by taurus on 2007-05-03
> **maso1870 said:**
> 
```
Filesystem            Size  Used Avail Use% Mounted on
/dev/sda5              23G   13G  9.1G  59% /
varrun                506M  136K  506M   1% /var/run
varlock               506M     0  506M   0% /var/lock
procbususb            506M  176K  506M   1% /proc/bus/usb
udev                  506M  176K  506M   1% /dev
devshm                506M     0  506M   0% /dev/shm
lrm                   506M   33M  473M   7% /lib/modules/2.6.20-15-generic/volatile
/dev/sda1              79G   31G   48G  40% /media/sda1
/dev/sda2              25G  3.3G   22G  14% /media/sda2
/dev/sda3              98G   81G   17G  84% /media/sda3
/dev/hdb              672M  672M     0 100% /media/cdrom0
[COLOR="Red"]/dev/sdb1             2.0G  234M  1.7G  12% /media/sdb1[/COLOR]
```


Your USB key is mounted to /media/sdb1 now.  

```
ls -la /media/sdb1
```

By the way, what does your /etc/fstab look like anyway?

```
cat /etc/fstab
```

---

### Post by maso1870 on 2007-05-03
Whoa, interestingly enough it's showing up under Computer now! I've unplugged/replugged, even rebooted and it seems to be working! 

Thanks Taurus,

cole

---

