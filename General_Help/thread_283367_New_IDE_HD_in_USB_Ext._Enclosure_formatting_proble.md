---
title: "New IDE HD in USB Ext. Enclosure formatting problem"
date: 2006-10-24
forum: General Help
---

### Post by wbeck85 on 2006-10-24
The internal hd on my laptop quit on me, so it is currently being RMA'd. The week before it died, I purchased a 250gb Western Digital Caviar EIDE WD2500 hard drive. I recieved it today. However, with this drive I recieved no documentation or drivers. I didn't think this was a problem. Note that the only computer I have is my laptop. So I mounted this IDE drive in my external enclosure (Bytecc something or other) and plugged it into my Dapper 6.06.1 LiveCD session. I expected to open up Gparted and format this drive to ext3 like any other drive I've had. However, that was not possible.

GParted lists the drive (/dev/sda) as having -2.74 MB of unallocated space. Negative 2.74 MB?? That doesn't make sense. So I tried ```
sudo fdisk -l /dev/sda
``` and that yielded ```
Disk /dev/sda: 2199.0 GB, 2199023254016 bytes
255 heads, 63 sectors/track, 267349 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

``` I do not think that this drive has 2.2 terabytes of storage space (though it would be nice). It seems to me that this is some USB / SCSI drive issue.

Basically, the greatest issue is that I cannot format this disk, so basically it is a brick sitting here. I think it may be possible if I had the thing hooked up with IDE in a standard desktop, but unfortunately I have none. Does anyone know why this may be, and/or how to get this thing working??

Your help is greatly appreciated!


Thank you,

~Will

---

### Post by bb002 on 2006-10-26
My guess is the problem is your external enclosure. I'm not saying your enclosure is faulty but that it may not support drives over a certain size. I spent a week helping a friend with this exact problem. I finally managed to get response back from a tech guy stating the particular model of his enclosure didn't support drives greater than 160GB.

I found the website [www.byteccusa.com](www.byteccusa.com)
I looked at the laptop hdd exclosures and their max supported hdd sizes. Most of the laptop hdd enclosures only support up to 160GB the rest are either 80GB or 100GB.

---

