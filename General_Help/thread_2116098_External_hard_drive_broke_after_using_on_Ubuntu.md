---
title: "External hard drive broke after using on Ubuntu"
date: 2013-02-14
forum: General Help
---

### Post by Instinct408 on 2013-02-14
I have a 2tb external harddrive which I use mainly on Windows 7. I have 2 separate hard drives in my computer, one for Windows 7 and the other for Ubuntu. My hard drive was working fine until I tried to use it on Ubuntu. There was no problem when I try to access the harddrive on Ubuntu but when I switched back to Windows 7, I cannot access it anymore. 

On Windows 7, I see my drive and the letter in My Computer but when I try to open it, it tries to load and eventually freezes the "My Computer" window. This then causes my "system" to crash and I need to restart. 

My hard drive works perfectly fine on Ubuntu but I can't open it on Windows 7. I have tried the manage Hard Drive utility on windows 7 but it gets stuck in the "detecting drives" and eventually freezes.

I formatted the drive to NTFS because I thought it would be compatible for both OS.

This has happened to me before and I fixed it by copying everyone over to another hard drive on Ubuntu. This is really an inconvenient because the drive is pretty big.

Does anyone know what is causing this? And maybe a possible fix?

---

### Post by LilLZ on 2013-02-14
When Ubuntu installs it reformats and partitions the drive anyways. All the partitions will be in linux (ext) format, which Windows cannot read. Odd that it crashes your system, though.

Edit: Reread this. Is the external drive just for storage or is that what Ubuntu is installed on?

---

### Post by Mark Phelps on 2013-02-15
What I would suggest is the following:
1) Download and burn a CD of the Minitool Partition Wizard Boot CD.  This is a Windows-based partitioning tool.
2) Boot your PC from that
3) Connect the external drive -- but do NOT open it
4) Use the menus in Partition Wizard to see if it will let you run a Check on the external drive.  IF it does, that is likely to fix it.

IF that doesn't work, you would need to consider using Data Recovery apps to get your data off the drive.

---

### Post by Instinct408 on 2013-02-15
> **LilLZ said:**
> When Ubuntu installs it reformats and partitions the drive anyways. All the partitions will be in linux (ext) format, which Windows cannot read. Odd that it crashes your system, though.

Edit: Reread this. Is the external drive just for storage or is that what Ubuntu is installed on?

To clarify, the external drive is just for data storage, no OS is installed. I originally formatted the drive on my windows 7 and have been using it there for a while. I use Ubuntu for school work and when I switched over to Ubuntu (same desktop) the drive was still working. But when I switched back to window 7, it was detected but I cannot open it. It causes my explorer to crash.

---

### Post by Instinct408 on 2013-02-15
> **Mark Phelps said:**
> What I would suggest is the following:
1) Download and burn a CD of the Minitool Partition Wizard Boot CD.  This is a Windows-based partitioning tool.
2) Boot your PC from that
3) Connect the external drive -- but do NOT open it
4) Use the menus in Partition Wizard to see if it will let you run a Check on the external drive.  IF it does, that is likely to fix it.

IF that doesn't work, you would need to consider using Data Recovery apps to get your data off the drive.

I could do this but this will not fix the problem. Once I fix the external drive and load it on Ubuntu, my windows 7 side will still not recognize it.

I am thinking Ubuntu changes the HD's format or permission? If that is the case maybe I can format the drive to a format that is compatible with both. I know NTFS is but I'm not sure what is going on.

---

### Post by Mark Phelps on 2013-02-15
> **Instinct408 said:**
> I could do this but this will not fix the problem. Once I fix the external drive and load it on Ubuntu, my windows 7 side will still not recognize it.
Then ,,, try mounting the external drive read-only and see what that does.

> I am thinking Ubuntu changes the HD's format or permission? 
NO, it does not.  While it will attempt to mount a partition read-write, and will update file date-timestamps if you change files, it does not change filesystem permissions.

> If that is the case maybe I can format the drive to a format that is compatible with both. I know NTFS is but I'm not sure what is going on.
Usually, the problem is that folks simply unplug and/or disconnect an external drive (formatted NTFS) in Ubuntu -- and if writes are pending, that can corrupt the NTFS filesystem, such that, when you reconnect the drive in Win7, you don't see the usual Windows Explorer window opening for the drive.  That doesn't mean that win7 doesn't SEE the drive, instead, it means that Win7 didn't assign it a letter.  To fix that, you go into Disk Management, scroll down until you see the drive and use the option to assign a Drive Letter.  IF that works, you'll see the Windows Explorer window open for the drive.

---

### Post by Joao Lacerda on 2013-02-15
I have fixed similar problem refreshing the partition table, that is something that you can look for. 

Good luck

---

### Post by Instinct408 on 2013-02-15
> **Mark Phelps said:**
> 
Usually, the problem is that folks simply unplug and/or disconnect an external drive (formatted NTFS) in Ubuntu -- and if writes are pending, that can corrupt the NTFS filesystem, such that, when you reconnect the drive in Win7, you don't see the usual Windows Explorer window opening for the drive.  That doesn't mean that win7 doesn't SEE the drive, instead, it means that Win7 didn't assign it a letter.  To fix that, you go into Disk Management, scroll down until you see the drive and use the option to assign a Drive Letter.  IF that works, you'll see the Windows Explorer window open for the drive.

When I try to open Disk Management, it tries to load the drives but nothing shows up. It says "connecting to Virtual Disk device" and nothing ever shows up. And my drive has a letter assigned to it, I can see the drive in My Computer but when I try to open it, it just freezes

---

### Post by Instinct408 on 2013-02-15
Here are some pics 

[http://imgur.com/a/DZBXl](http://imgur.com/a/DZBXl)

img 1) try to load

img 2) freeze

img 3) sometimes this happens after its done loading

---

### Post by carl4926 on 2013-02-16
From your windows terminal

```
chkdsk G:/f
```

Did you try?

---

### Post by MrsUser on 2013-02-16
I had this problem once when I was still a Windows user. And it turned out it was a virus that had the file system structure corrupted. If you have another storage drive available, I recommend to backup all your data, then reformat. But make sure you re-install Windows before using the drive with Windows again.

---

