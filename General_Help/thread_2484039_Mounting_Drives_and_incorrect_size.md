---
title: "Mounting Drives and incorrect size"
date: 2023-02-16
forum: General Help
---

### Post by paulies on 2023-02-16
Hi,

I have an 8tb drive and mounts just fine showing I have used 4 % of my free space but after about an hour or 2 it changes and says I have used 96% of my free space un mounting and mounting again fixes the problem. Does anyone one how I can fix this or even why it changes in the first place.

Thanks Paul

---

### Post by ActionParsnip on 2023-02-16
What file system are you using? Ext4? XFS? Are you using LVM?

---

### Post by paulies on 2023-02-16
I’m using ext4 and not using lvm 

Never had this problem before it’s very odd

---

### Post by ActionParsnip on 2023-02-16
What is the output of
```

sudo parted -l; df -Th; lsb_release -a; uname -a

``` 
Thanks

---

### Post by paulies on 2023-02-17
> **ActionParsnip said:**
> What is the output of
```

sudo parted -l; df -Th; lsb_release -a; uname -a

``` 
Thanks

Hi the output is this

/dev/sda1      vfat       99M  6.1M   93M   7% /boot/efi
/dev/sdb1      ext4      3.6T  2.2T  1.3T  63% /mnt/usb1
/dev/sdf1      ext4      5.5T  3.0T  2.3T  58% /mnt/usb3
/dev/sdc1      ext4      7.3T  4.3T  2.6T  63% /mnt/usb2
/dev/sdg1      ext4      5.5T  3.3T  2.0T  63% /mnt/usb4
tmpfs          tmpfs     779M   24K  779M   1% /run/user/1000
/dev/sdd1      ext4      219G   67G  141G  33% /media/paul/OS_Backup
/dev/sde1      ext4      7.3T  6.9T     0 100% /mnt/usb5
No LSB modules are available.
Distributor ID: Ubuntu
Description:    Ubuntu 20.04.5 LTS
Release:        20.04
Codename:       focal

From what I understand it say I’m using all the space put on the disks app on the gui I’m only using 4% of the space 1.4tb on check the files the disk app is correct until another hour passes and it goes back to how it was.

---

### Post by ActionParsnip on 2023-02-17
Use UUIDs. Don't use device names like that. You'll get fewer issues

---

### Post by paulies on 2023-02-17
> **ActionParsnip said:**
> Use UUIDs. Don't use device names like that. You'll get fewer issues

In fstab they all mount as uuids and point to ie usb1 or is that wrong ?

---

### Post by ActionParsnip on 2023-02-17
If you run:
```

sudo blkid

```
You will see the unique UUID for each file system. You can use these in /etc/fstab. These never change. The "sda" "sdb" stuff can change and so UUIDs are a good fix.

---

### Post by TheFu on 2023-02-17
> **paulies said:**
> I&#8217;m using ext4 and not using lvm 

Never had this problem before it&#8217;s very odd

How is this device physically connected?  SATA? SCSI, SAS, eSATA, Infiniband?

USB - yuck.  Those connections are known to be flaky.

---

### Post by paulies on 2023-02-18
Ive not had any trouble with the other drives so I have back up all the data and going to try and set the drive up again and see how it goes.

---

### Post by TheFu on 2023-02-18
> **paulies said:**
> Ive not had any trouble with the other drives so I have back up all the data and going to try and set the drive up again and see how it goes.

When connections disappear, that means there's something less than great with either the USB controller or with the physical USB connection.
I had a SATA connected external array where 1 drive kept dropping.  Replaced that SATA cable with a cable that has a 90° SATA connection. That fixed it.  
When I've had USB connections that would disappear, it has been due to either the USB chip in the usb-hub (which needed a firmware update) or a bad physical connection.  Slightly pressing in using a pair of pliers on the USB male connector (very slightly) made those connections more stable.  I learned a lesson.  Only use USB connections for backup storage, never primary.  My external primary storage is connected with either infiniband or eSATA and has been almost 15 yrs. This avoids dumb connection issues that make a system untrusted.

---

