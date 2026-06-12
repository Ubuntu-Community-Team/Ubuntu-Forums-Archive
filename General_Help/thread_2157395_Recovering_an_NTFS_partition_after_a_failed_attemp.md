---
title: "Recovering an NTFS partition after a failed attempt by Windows 7 to expand it"
date: 2013-06-25
forum: General Help
---

### Post by User4519 on 2013-06-25
Hi :)

So I have this 2TB external drive which held two 250GB HFS+ partitions for time machine backups + one 1.5 TB NTFS partition at the end of the drive containing some downloads.

I recently moved my time machine backups to iSCSI, so I wanted to delete the HFS+ partitions and expand the NTFS partition to use the entire drive.

Thinking the most NTFS-savvy and therefore safest OS would be Windows, I booted up Windows 7. I deleted the two HFS+ partitions and a small EFI partition which Mac OS X really loves to create for no good reason, and then I went and asked Windows to extend the NTFS partition. This failed pretty much immediately with some non-descriptive error which escapes me.

It did, however, have time to write a new GPT and hybrid MBR which looks like this:

```
Number  Start (sector)    End (sector)  Size       Code  Name
   1            2082            4129   1024.0 KiB  4201  LDM metadata partition
   2            4130          262177   126.0 MiB   AF00  Microsoft reserved part
   3          262178      3907029134   1.8 TiB     4200  LDM data partition
```

And now I have a defunct drive. I'm not sure what those two partitions at the start are for (guessing something the failed extend operation would need in order to complete its job?). I'm also not sure what to make of the "LDM data partition" stuff.

What I do know, is that I can no longer get any OS to recognize my NTFS partition on there. Naturally, I'd say, as that partition actually starts quite some number of sectors beyond [FONT=courier new]262178[/FONT] which GPT claims. So, any fs prober would just see some random data at the place it expects to see whatever it needs to see to determine FS type.

I'm not panicking yet (won't regardless, at it isn't exactly the **most** important stuff that's on there), but I'm a bit unsure what my next step should be. 

My previous step **should've **been backing up the GPT, but obviously I had to learn that the hard way.

Is there a clever way to scan the approximate area of where the NTFS partition actually starts for some kind of binary signature so that I can manually reconstruct the GPT?

Or perhaps another method which would help me reconstruct my partition/data?

Thanks in advance,
Daniel :)

---

### Post by philinux on 2013-06-25
Sounds like you need this [http://www.cgsecurity.org/wiki/TestDisk](http://www.cgsecurity.org/wiki/TestDisk)

testdisk is available to install from the software center. Good luck.

I would also wait for more replies before doing anything.

---

### Post by User4519 on 2013-06-25
> **philinux said:**
> Sounds like you need this [http://www.cgsecurity.org/wiki/TestDisk](http://www.cgsecurity.org/wiki/TestDisk)

testdisk is available to install from the software center. Good luck.

I would also wait for more replies before doing anything.

Looks really interesting. I'll play around with it for a bit. If it really can recover just the MBR/GPT without modifying other data, that'd be fantastic. If not, I may go with GetDataBack for NTFS, since I've previously used that with much success to get back lost data. Only thing is, it's horribly slow.

Thank you! :)

EDIT: It's analyzing, and very quickly discovered the deleted HFS+ partitions. Looking good :)

---

### Post by User4519 on 2013-06-25
Well, TestDisk started going slower and slower, then eventually froze (couldn't even Ctrl+C it). I'm gonna go with the slow but reliable GetDataBack.

But thanks for tipping me on TestDisk &#8212; I'll keep it around for future screwups ;)

---

### Post by oldfred on 2013-06-25
LDM is another name for dynamic partitions with Windows. Windows has dynamic partitions to get around the 4 primary partition limit on MBR(msdos) partitioned drives. With gpt I have no idea why they would even offer dynamic partitions.

       Dynamic also on gpt as LDM
[http://msdn.microsoft.com/en-us/library/windows/desktop/aa365449%28v=vs.85%29.aspx]("http://msdn.microsoft.com/en-us/library/windows/desktop/aa365449%28v=vs.85%29.aspx")

      
 Microsofts offical policy is a full backup, erase dynamic partitions and create new basic partitions. There is no undo.
Dynamic volume is a Microsoft proprietary format developed together with Veritas (now acquired by Symantec) for logical volumes.
You may be use a third-party tool, such as Partition Wizard MiniTool or EASEUS to convert a convert a dynamic disk to a basic disk without having to delete or format them.
I've never used any of these and so I can't be sure they will work.Be sure to have good backups as any major partition change has risks.
Dynamic also on gpt as LDM
[http://msdn.microsoft.com/en-us/library/windows/desktop/aa365449%28v=vs.85%29.aspx](http://msdn.microsoft.com/en-us/library/windows/desktop/aa365449%28v=vs.85%29.aspx)

   Used EASEUS Partition Master -  free version used to  include conversion
[http://ubuntuforums.org/showthread.php?t=1692248](http://ubuntuforums.org/showthread.php?t=1692248)
EASEUS Partition Master - The free home edition converted both dynamic partitions into basic partitions in less than 5 minutes!!
[http://www.partition-tool.com/personal.htm](http://www.partition-tool.com/personal.htm)

   Several users have used this, it has a liveCD download to use but you have to use the non-free version:
MiniTool Partition Wizard Professional Edition 5.2 to convert without loss of data the disk from dynamic disk to a basic disk.
also used Partition Wizard to set an existing partition logical instead of primary
Converted from dynamic with MiniTool, & repaired windows
[http://ubuntuforums.org/showthread.php?t=1779529](http://ubuntuforums.org/showthread.php?t=1779529)
[http://www.partitionwizard.com/convertpartition/convert-to-basic-disk.html](http://www.partitionwizard.com/convertpartition/convert-to-basic-disk.html)
Partition wizard repaired NTFS partition table that gparted could not see with disk label error
[http://ubuntuforums.org/showthread.php?t=2112005](http://ubuntuforums.org/showthread.php?t=2112005)

---

### Post by User4519 on 2013-06-27
> **oldfred said:**
> LDM is another name for dynamic partitions with Windows. Windows has dynamic partitions to get around the 4 primary partition limit on MBR(msdos) partitioned drives. With gpt I have no idea why they would even offer dynamic partitions.

Hi Oldfred, thanks for your reply :)

And sorry for the long quiet on my part — I was in Windows on a two-day recovery of the data using GetDataBack. It succeeded, every bit was recovered, but dang, it's slow ;)

Now that you mention it, I do remember that Windows said it needed to convert the disk to dynamic, and I just let it. That may have been what screwed it up. I kinda assumed it was just Microsoft-speak for GPT, but I can see how GPT+Hybrid MBR+MS Dynamic stuff could really mess things up :D

And I agree, I can't see why they'd want to use that stuff when GPT is around. Except, of course, for legacy reasons. Oh, and I remember something about LVM and MD-like features that were available with dynamic disks. Still doesn't make much sense to use it on a single disk except when absolutely necessary.

It's not for me, though. Gimme my MBRs for the simple disks and GPTs for the more advanced stuff ;)

Cheers!

---

