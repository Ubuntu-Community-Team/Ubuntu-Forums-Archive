---
title: "Deleted everything in SDA1 how to recover?"
date: 2014-12-28
forum: General Help
---

### Post by sendbrianspam on 2014-12-28
OK, I'm a dumbass.  I thought I was deleting my USB drive, but it wasn't.  I highlighted everything in SDA1 and hit delete.  I remember there was a boot folder, and a bunch of other stuff.  Like I said, I thought it was a USB drive and figured it was a UBUNTU live CD or some such thing.  I checked in my "Trash", and it's not there.  

My computer is still on, and it works fine, but I know if I reboot, it won't work.  How do I know?  I did this once before (like I said, I'm a dumbass sometimes).  Last time, I spend like a day and a half trying to fix it.  I did so many things and tried so many recovery tools, I don't know what combination it actually took to fix it.  Since I'm seeing it earlier now, I figure there is a simpler solution, but could really use some guidance on what to do to troubleshoot and fix.

I am running a laptop with dual boot Windows 8 and Ubuntu 14.04.  I'm currently running Ubuntu, and won't turn it off until I think I've got it fixed. 

The information on the drive I can see in properties :  name: sda1   Type: Folder (inode/directory)  Contents: nothing  Location: /media  Volume : sda1
26.7 MB used   340.3 MB free Total capacity : 367 MB


```
brian@brian-X202E:/media/sda1$ sudo fdisk -l
[sudo] password for brian: 


Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes
Disk identifier: 0x737250dc


   Device Boot      Start         End      Blocks   Id  System
/dev/sda1            2048      718847      358400    7  HPFS/NTFS/exFAT
/dev/sda2   *      718848   720476159   359878656    7  HPFS/NTFS/exFAT
/dev/sda3       720476160   976771071   128147456    5  Extended
/dev/sda5       720478208   968617983   124069888   83  Linux
/dev/sda6       968622080   976771071     4074496   82  Linux swap / Solaris
```




If anyone has any advice on what to run or things to check and post back, please help.

Thanks

---

### Post by HermanAB on 2014-12-28
There is no perfect way to fix it. Use photorec to recover pics and re-install.

---

### Post by Bucky Ball on 2014-12-28
Testdisk may also help. See these links:

[http://www.cgsecurity.org/](http://www.cgsecurity.org/)

Testdisk description:
[http://www.cgsecurity.org/wiki/TestDisk](http://www.cgsecurity.org/wiki/TestDisk)

Photorec description:
[http://www.cgsecurity.org/wiki/PhotoRec](http://www.cgsecurity.org/wiki/PhotoRec)

Main thing is, don't use that disk. Boot from Live media. 

PS: I have added [code] tags to your first post. Please use them for terminal/code output. Thanks. ;)

---

### Post by sendbrianspam on 2014-12-28
Thank you.  TestDisk was able to recover all the deleted files.  Quite a relief!

---

### Post by Bucky Ball on 2014-12-28
> **sendbrianspam said:**
> Thank you.  TestDisk was able to recover all the deleted files.  Quite a relief!

Yea. It's well handy. Good news. ;)

---

### Post by dragonfly41 on 2014-12-28
Not really relevant now ... but after the mishap if the OP had opened Rubbish Bin (Trash) and clicked on
"Restore Selected Items" .. would that have worked?

> 
I highlighted everything in SDA1 and hit delete.  I remember there was a  boot folder, and a bunch of other stuff.  Like I said, I thought it was  a USB drive and figured it was a UBUNTU live CD or some such thing.  I  checked in my "Trash", and it's now there.

---

### Post by ajgreeny on 2014-12-28
I am also confused as to why the partition is mounted at /media, and why testdisk was needed if the files were just in trash.
Which trash?  If this was a disk mounted in media it would normally have its own hidden trash folder; files would not go to the user's trash.
Is this a Windows partition which you mount at boot with an entry in /etc/fstab?

---

### Post by sendbrianspam on 2014-12-28
> **dragonfly41 said:**
> Not really relevant now ... but after the mishap if the OP had opened Rubbish Bin (Trash) and clicked on
"Restore Selected Items" .. would that have worked?

Good question.   I had a typo in my OP.  I originally typed > [COLOR=#000000] I checked in my "Trash", and it's now there. 

[/COLOR]I would have tried to "restore selected items" and suspect it would have worked.

In reality, the situation was  > [COLOR=#000000] I checked in my "Trash", and it's NOT there. [/COLOR]

---

### Post by sendbrianspam on 2014-12-28
> **ajgreeny said:**
> I am also confused as to why the partition is mounted at /media, and why testdisk was needed if the files were just in trash.
Which trash?  If this was a disk mounted in media it would normally have its own hidden trash folder; files would not go to the user's trash.
Is this a Windows partition which you mount at boot with an entry in /etc/fstab?

I explained my typo in the previous post.  I checked my user trash.  If there his a hidden trash folder somewhere else associated with my sda1, I was not aware of that. Is it odd that it's mounted as /media?  Should I change something?  If it wasn't even visible to me, then I'd be even less likely to make a similar mistake again.  Hopefully I don't anyway.

 Yes, this is a NTFS partition.  It has these files/folders:  

>  bcd  Boot  bootmgr  BOOTNXT  System Volume Information  Temp 

---

### Post by sendbrianspam on 2015-01-08
Can anyone tell me if there is a reason that my sda1 (Windows BCD)  needs to be mounted when I run Linux?  If not, how can I stop it from getting mounted?

---

### Post by Bucky Ball on 2015-01-08
Remove the entry for it from /etc/fstab. ;)

---

