---
title: "USB hard drive switching to read only"
date: 2007-01-18
forum: General Help
---

### Post by Richey on 2007-01-18
Hi everyone,

I've been using Ubuntu (Dapper) for a few months now and absolutely love it, however I have recently had the problem of my 250gb USB Hard Disk (Western Digital) seems to randomly set itself to be read only after a few hours use. I only noticed when aMule displayed an error messgae saying it couldnt write to the drive anymore.

I have tried the drive in Windows XP and it seems to read and wrtie fine.

Anyone had a similar problem or know of any potential solution?

Thanks in advance

Rich

---

### Post by lukew on 2007-01-18
> **Richey said:**
> Hi everyone,

I've been using Ubuntu (Dapper) for a few months now and absolutely love it, however I have recently had the problem of my 250gb USB Hard Disk (Western Digital) seems to randomly set itself to be read only after a few hours use. I only noticed when aMule displayed an error messgae saying it couldnt write to the drive anymore.

I have tried the drive in Windows XP and it seems to read and wrtie fine.

Anyone had a similar problem or know of any potential solution?

Thanks in advance

Rich

it will remount as readonly when there are errors. I presume ( seeing as you can write to it from windows ) that it is vfat or someting similar.

I would run fsck on the disk.

Luke

---

### Post by Richey on 2007-01-18
Hi thanks for your reply.

Should have probably pointed out that the drive is FAT32 so I can't run fsck on it.

Rich

---

### Post by lukew on 2007-01-18
> **Richey said:**
> Hi thanks for your reply.

Should have probably pointed out that the drive is FAT32 so I can't run fsck on it.

Rich

Thats not true. It fsck is just a see through to fsck.ext and fsck.vfat etc.

Luke

---

### Post by Richey on 2007-01-18
Ahh didn't know that, thanks alot I'll give it a go.

Rich

---

### Post by Richey on 2007-01-18
Right I've tried to run fsck.vfat from the terminal using the command:

fsck.vfat -t -r /dev/sda

It's giving me the error:

dosfsck 2.11, 12 Mar 2005, FAT32, LFN
Currently, only 1 or 2 FATs are supported, not 251.

Any idea why this is, apologies if this sounds stupid I rarely delve into the terminal stuff.

Rich

---

### Post by lukew on 2007-01-18
> **Richey said:**
> Right I've tried to run fsck.vfat from the terminal using the command:

fsck.vfat -t -r /dev/sda

It's giving me the error:

dosfsck 2.11, 12 Mar 2005, FAT32, LFN
Currently, only 1 or 2 FATs are supported, not 251.

Any idea why this is, apologies if this sounds stupid I rarely delve into the terminal stuff.

Rich

Can you:

```
fdisk -l
```

Just to check what type of partition it is.

Also ( on a side note ) you did unmount the partition first?

Cheers

Luke

---

### Post by lukew on 2007-01-18
> **Richey said:**
> Right I've tried to run fsck.vfat from the terminal using the command:

fsck.vfat -t -r /dev/sda

It's giving me the error:

dosfsck 2.11, 12 Mar 2005, FAT32, LFN
Currently, only 1 or 2 FATs are supported, not 251.

Any idea why this is, apologies if this sounds stupid I rarely delve into the terminal stuff.

Rich

I think you should be running this against somethign like /dev/sda1 i.e the parition and not the device.

Luke

---

### Post by BathroomNinja on 2007-01-19
fsck.vfat -t -r /dev/sdc1 fixed my Sansa e250 that was only mounting as read only!  Hoorah!

---

### Post by Karbonik on 2007-03-27
Thank you very much!  This solution worked for me on my Eltec 4.0 Gig Flash drive which suddenly decided to go readonly.

I also noticed that I had trouble with this to two different drives yesterday, and I have a feeling that this might be a pervasive issue... will I have to run 
fsck.vfat -t -r /dev/sdc  on the other usb disks that weren't working?

---

