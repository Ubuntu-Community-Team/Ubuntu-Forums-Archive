---
title: "VMware using your other partition"
date: 2008-02-11
forum: General Help
---

### Post by DizzyThermal on 2008-02-11
Hey guys, I have been using VMware to use Windows in Ubuntu and it worked until I wanted to use it with the other Partition instead of rebooting

I followed this tutorial: [http://oopsilon.com/Running-a-Windows-Partition-in-VMware](http://oopsilon.com/Running-a-Windows-Partition-in-VMware)

At the point where it says to fire up VMware it has an error saying Couldn't find WindowsXP.vmdk  which is in the same folder as the WindowsXP.vmx

I got all the values right too...

When I hit browse to find it, it doesn't work either...

Anyone ever get this error?  Help please!  Thanks in advance! :)

**Solved!**
====================================
**Unmounted the windows partition:**

```
sudo su
umount -a
```

**Changed the permissions on the mount:**

```
sudo su
cd /media
chown dizzy windows
```

***Note*: Keep the partition _unmounted_***

This worked for me guys :)
====================================

---

### Post by DizzyThermal on 2008-02-12
Anyone? Please? :(

---

### Post by DizzyThermal on 2008-02-14
I take it that nobody knows..?

I mean someone has to have had this problem before... :-\

---

### Post by dcstar on 2008-02-14
> **DizzyThermal said:**
> Hey guys, I have been using VMware to use Windows in Ubuntu and it worked until I wanted to use it with the other Partition instead of rebooting

I followed this tutorial: [http://oopsilon.com/Running-a-Windows-Partition-in-VMware](http://oopsilon.com/Running-a-Windows-Partition-in-VMware)

At the point where it says to fire up VMware it has an error saying Couldn't find WindowsXP.vmdk  which is in the same folder as the WindowsXP.vmx

I got all the values right too...

When I hit browse to find it, it doesn't work either...

Anyone ever get this error?  Help please!  Thanks in advance! :)

Manually stuffing around with files instead of allowing WMware to create them causes issues like this. Instructions like that are based on various assumptions that may be valid for a specific distro/environment, but won't work with others.

If you want to be sure things will work in Ubuntu, find a Ubuntu tutorial (not a Gentoo one).

Check the permissions of the files you manually created - if VMware can't see them then it can't use them.

---

### Post by DizzyThermal on 2008-02-15
Thanks for the reply, I felt like people we just ignoring me.

This is like the only tutorial I could find...  Not easy finding a specific tutorial like this.

---

### Post by mbeierl on 2008-02-15
How 'bout giving us a little more to go on, like the content of your .vmx file and the output of "sfdisk -l" (or some other way of telling what your partitions are)?  I'd be glad to help...

---

### Post by DizzyThermal on 2008-02-16
sfdisk -l:
```
Disk /dev/hda: 38913 cylinders, 255 heads, 63 sectors/track
Units = cylinders of 8225280 bytes, blocks of 1024 bytes, counting from 0

   Device Boot Start     End   #cyls    #blocks   Id  System
/dev/hda1   *      0+  17846   17847- 143355996    7  HPFS/NTFS
/dev/hda2      17847   38535   20689  166184392+  83  Linux
/dev/hda3      38536   38912     377    3028252+   5  Extended
/dev/hda4          0       -       0          0    0  Empty
/dev/hda5      38536+  38912     377-   3028221   82  Linux swap / Solaris

```

WindowsXP.vmx:
```
config.version = "8"
virtualHW.version = "4"

uuid.location = "56 4d 56 4a 7b d7 4c 30-f5 80 d6 8b c4 59 aa eb"
uuid.bios = "56 4d 56 4a 7b d7 4c 30-f5 80 d6 8b c4 59 aa eb"

uuid.action = "create"
checkpoint.vmState = ""

displayName = "Windows XP Professional"
annotation = ""
guestinfo.vmware.product.long = ""
guestinfo.vmware.product.url = ""

guestOS = "winxppro"
numvcpus = "1"
memsize = "192"
paevm = "FALSE"
sched.mem.pshare.enable = "TRUE"
MemAllowAutoScaleDown = "FALSE"

MemTrimRate = "-1"

nvram = "WindowsXP.nvram"

mks.enable3d = "FALSE"
vmmouse.present = "FALSE"
vmmouse.fileName = "auto detect"

tools.syncTime = "TRUE"
tools.remindinstall = "FALSE"

isolation.tools.hgfs.disable = "FALSE"
isolation.tools.dnd.disable = "FALSE"
isolation.tools.copy.enable = "TRUE"
isolation.tools.paste.enabled = "TRUE"
gui.restricted = "FALSE"

ethernet0.present = "TRUE"
ethernet0.connectionType = "nat"
ethernet0.addressType = "generated"
ethernet0.generatedAddress = "00:0c:29:59:aa:eb"
ethernet0.generatedAddressOffset = "0"

usb.present = "TRUE"
usb.generic.autoconnect = "TRUE"

sound.present = "TRUE"
sound.virtualdev = "sb16"

ide0:0.present = "TRUE"
ide0:0.fileName = "WindowsXP.vmdk"
ide0:0.mode = "independent-persistent"
ide0:0.deviceType = "rawDisk"
ide0:0.redo = ""
ide0:0.writeThrough = "FALSE"
ide0:0.startConnected = "TRUE"

ide1:0.present = "TRUE"
ide1:0.fileName = "/dev/cdrom"
ide1:0.deviceType = "atapi-cdrom"
ide1:0.writeThrough = "FALSE"
ide1:0.startConnected = "TRUE"

floppy0.present = "TRUE"
floppy0.fileName = "/dev/fd0"
floppy0.startConnected = "TRUE"

serial0.present = "FALSE"
serial1.present = "FALSE"
parallel0.present = "FALSE"
```

WindowsXP.vmdk:
```
# Disk DescriptorFile
version=1
CID=9428f535
parentCID=ffffffff
createType="fullDevice"

# Extent description
RW 63 FLAT "WindowsXP.mbr" 0
RW 625142384 FLAT "/dev/hda" 63

# The Disk Data Base
#DDB

ddb.toolsVersion = "6530"
ddb.adapterType = "ide"
ddb.virtualHWVersion = "4"
ddb.geometry.sectors = "63"
ddb.geometry.heads = "255"
ddb.geometry.cylinders = "38913"
```

If you need anything else I can give it to you :)  Thanks for giving me hope! :D

---

### Post by mbeierl on 2008-02-17
Yep.  What're the permissions on /dev/hda?  Your userid probably does not have direct access to the raw device - and that's who you run vmware as...

---

### Post by zvacet on 2008-02-17
Read [this](http://news.u32.net/articles/2006/07/18/running-vmware-on-a-physical-partition) and see if can be of any help to you.

---

### Post by DizzyThermal on 2008-02-18
The permissions are for "root"

I wouldn't know how to change that though.

I have it mounted in media/windows.

Meaning I have an icon on my desktop that is called "windows"

I right click it and the permissions are root.

So would I:

```
sudo su
*password*
cd /
cd home/dizzy/Desktop
chown dizzy windows
```

Would it be like that or something else?

Plus, I don't think it's an issue of permissions, it just can't find it....   "Can't find WindowsXP.vmdk"  [Browse]

+++++++++++++++

Yes I have read that tutorial but it wants me to use VMware Server and I don't have that :\

---

### Post by DizzyThermal on 2008-02-18
**Solved:**

**Unmounted the windows partition:**

```
sudo su
umount -a
```

**Changed the permissions on the mount:**

```
sudo su
cd /media
chown dizzy windows
```

***Note*: Keep the partition _unmounted_***

This worked for me guys :)

---

