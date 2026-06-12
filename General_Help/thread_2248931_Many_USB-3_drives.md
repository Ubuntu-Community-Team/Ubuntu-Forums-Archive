---
title: "Many USB-3 drives"
date: 2014-10-18
forum: General Help
---

### Post by ELMIT on 2014-10-18
I got into my pc extra PCI-e cards which expands for 4 USB3 ports.
I also got USB3 hubs.

I got many USB-3 drives, which are only read one at a time.

I got a directory on each USB-3    /data
This directory may hold one or more files.

I got a directory in my home directory   /data


**_Questions:_**
1. How many hard disks can I attach to the system, if I use USB3 port of the computer => USB3 hub => ? => hard disk
How deep can I cascade? How does one branch (amount) influence the other branches?


2. I need the files in the   /data directory   ???   to the  home directory/data/
For  ???    I used  ln -s 

I do not know how many drives I will attach, maybe I will need to add one later.
I hope there is a way to find the new drives and automount it.

The drives look all the same, just the file in the directory data have a different UNIQUE name.
Is there a better way then ln -s drive/data/file1 homedir/data/   ?

I also do not know the squence the drives are attached, which would change the /dev/sd<?>1 and so the unique file name


3. Ubuntu 14.04 automounts two of the multple drives automatically, and leaves the others unmounted, but recognizes them as:
/dev/sdb1, /dev/sdc1, /dev/sdd1 .... and the last two will be auto mounted. (/dev/sda1 is the OS)
I need all mounted. 
How can I do that?
How many hard disks can Ubuntu recognize at all? /dev/sdz1 ??? and then?
Do I need to prepare devices?


4. What happens when I detach one drive? Is just the file of that drive's /data directory lost? What happens when I attach one drive (maybe the same, maybe another one)?

---

### Post by TheFu on 2014-10-18
USB spec says 127 devices are supported, but there are vast differences in what the spec says and what firmware, drivers, hardware really supports.  Plus larger numbers won't be tested as thoroughly has fewer.

It is unclear to me if that 127 limit is per host, per controller, per port .... 

For storage, I use either UUIDs or Labels to determine mount locations. Don't use /dev/sd?? stuff anymore. **blkid** will return the xref or just look at the links generated at boot/connection under /dev/disk/by-*  
For my systems, every device gets a different mount point under /D data for me using autofs. Using autofs (automounter) solves many concerns you have listed above.  

Not all devices work with hubs. I've had HDDs refuse to work through any hub and others are happy.  On one system I had to disable all USB2 ports for USB3 to work at all. There are forum posts about that here.

---

### Post by ELMIT on 2014-10-18
I read about the 127 devices for USB-2.0, and it would be sufficient if it is per computer ;-)
However, I have not read that it would be valid for USB-3.0

> For storage, I use either UUIDs or Labels to determine mount locations. Don't use /dev/sd?? stuff anymore. blkid will return the xref or just look at the links generated at boot/connection under /dev/disk/by-*
For my systems, every device gets a different mount point under /D data for me using autofs. Using autofs (automounter) solves many concerns you have listed above.


Unfortunately these Seagate devices harddisks have a fixed label and a fixed UUID, but ALL drives the same!!! I have not found a way to change UUID or label for these drives, since it is NTFS. All tools I found are for not-NTFS.

How to use autofs?

dmesg |grep Seag
[    6.152788] usb 11-1: Manufacturer: Seagate
[   10.598624] usb 11-2.1: Manufacturer: Seagate 
[   10.692910] usb 11-2.2: Manufacturer: Seagate
[   10.788840] usb 11-2.3: Manufacturer: Seagate
[   10.882581] usb 11-2.4: Manufacturer: Seagate 
[   22.235626] scsi 6:0:0:0: Direct-Access     Seagate  Expansion Desk   0604 PQ: 0 ANSI: 6
[   22.235672] scsi 7:0:0:0: Direct-Access     Seagate  Expansion Desk   0739 PQ: 0 ANSI: 6
[   22.239696] scsi 10:0:0:0: Direct-Access     Seagate  Expansion Desk   0739 PQ: 0 ANSI: 6
[   22.240153] scsi 9:0:0:0: Direct-Access     Seagate  Expansion Desk   0604 PQ: 0 ANSI: 6
[   22.240158] scsi 8:0:0:0: Direct-Access     Seagate  Expansion Desk   0604 PQ: 0 ANSI: 6

Can we do something with this information?
usb 11-1   seems the drive directly on the USB3 port
usb 11-2.x seems to be the 4 drives on the hub

---

### Post by TheFu on 2014-10-18
I would expect any partitioning tool would be able to change the disk label.

Using the USB path might work, if you guarantee the same port will always (and only) be used for the same HDD/partitions.  I wouldn't assume that.

USB3 device limits are either the same or larger than USB2. I couldn't find the limit for USB3 either, but only looked for 5 minutes.

autofs is about mounting only when needed - nothing more. I find it great for NFS and USB storage.

Do you want the disks to be identical?
Do you want more than 1 at a time connected?
I'd be shocked if the UUID were identical even on identical models, versions, with identical labels - that is why UUIDs were created. Seems the serial number would prevent that from happening. OTOH,  I dunno. I avoid buying identical storage.

---

### Post by Dennis N on 2014-10-18
> I have not found a way to change UUID or label for these drives, since it is NTFS. All tools I found are for not-NTFS.

Try **ntfslabel**

from the man page:
> ntfslabel will display or change the file system label on the ntfs file system located on device.  It can also change the serial number of  the device. ntfslabel will display or change the file system label on the ntfs file system located on device.  It can also change the serial number of  the device.


---

