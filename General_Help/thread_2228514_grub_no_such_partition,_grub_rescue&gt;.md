---
title: "grub: no such partition, grub rescue&gt;"
date: 2014-06-07
forum: General Help
---

### Post by broaff on 2014-06-07
Hi, i have this error when i want to boot up my pc. It looks like my partition table is damaged, if i check it with gparted i only see a big unallocated thing. (*Can't have a partition outside the disk!)*

This is the response of a fdisk -l:

```
Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *        2048   129049008    64523480+   7  HPFS/NTFS/exFAT
/dev/sda2       129050145   972580863   421765359+   f  W95 Ext'd (LBA)
/dev/sda3       972580864   976769023     2094080    c  W95 FAT32 (LBA)
/dev/sda5       129050208   778011947   324480870    7  HPFS/NTFS/exFAT
/dev/sda6   ?  1081629323   169915629  1691626801+  b9  Unknown
```

I have one partition for win7, one for data, one for ubuntu + recovery partition.
I tried a few guides but i always end up in errors. The problem is that i don't understand what i'm doing. Is there a way to fix this? Could you help me and give me exact commands that will repair this? I don't care about my linux partition, i just want to boot into my win7. :(

Thanks

---

### Post by oldfred on 2014-06-08
It looks like you have a totally invalid start sector on sda6.

       Backup partition table structure to text file & save to external device.
sudo sfdisk -d /dev/sda > PTsda.txt

You can manually edit the PTsda.txt, but it uses start & size not start & end data.

I might try fixparts first to see if it will update partition table entries.

      
 Fixparts - Repair broken partition tables (not overlapping issues) & delete Stray gpt data from MBR drives
[http://ubuntuforums.org/showthread.php?t=1667614&p=10367957#post10367957](http://ubuntuforums.org/showthread.php?t=1667614&p=10367957#post10367957)
[http://ubuntuforums.org/showthread.php?t=1705325](http://ubuntuforums.org/showthread.php?t=1705325) 
[http://www.rodsbooks.com/fixparts/](http://www.rodsbooks.com/fixparts/)

---

### Post by broaff on 2014-06-08
Thank you very much for your response.

The following happens:

fixparts /dev/sda
```
FixParts 0.8.8

Loading MBR data from /dev/sda
Unable to seek to 2178183608! Aborting!
EBR signature for logical partition invalid; read 0xB8CF, but should be 0xAA55
Error reading logical partitions! List may be truncated!

Warning: 0xEE partition doesn't start on sector 1. This can cause problems
in some OSes.
Warning: Deleting oversized partition #6! Start = 1081629323, length = 3383253603
```

With command p:

```
Disk size is 976773168 sectors (465.8 GiB)
MBR disk identifier: 0x43FF71A6
MBR partitions:

                                                   Can Be   Can Be
Number  Boot  Start Sector   End Sector   Status   Logical  Primary   Code
   1      *           2048    129049008   primary     Y        Y      0x07
   3             972580864    976769023   logical     Y        Y      0x0C
   5             129050208    778011947   logical     Y        Y      0x07

```

Command w:

```
Final checks complete. About to write MBR data. THIS WILL OVERWRITE EXISTING
PARTITIONS!!

Do you want to proceed? (Y/N): y

Warning: 0xEE partition doesn't start on sector 1. This can cause problems
in some OSes.
Done writing data!
```

Phew. Now i restart. [-o<

Edit: new error message at startup: grub: unknow filesystem, grub rescue>

Edit2: Wohoo! I see some kind of progress. In the result of previous actions the big unallocated thing disappeared.
[IMG]http://s29.postimg.org/99p0eqfmf/asd.png[/IMG]

Extra info: that unallocated partition was my ubuntu partition.



I made a stupid thing, i tried to make a 10MB partition from the unallocated to make a new grub there but this happens:
[http://s8.postimg.org/gs1x7kms5/asd2.png](http://s8.postimg.org/gs1x7kms5/asd2.png)

---

### Post by oldfred on 2014-06-08
You deleted the Linux partition which had the rest of grub including menu. You can either repair partition table with correct start for Linux partition so it can boot with grub with testdisk or restore a Windows boot loader.

I had hoped that fixparts might just reset start also, but it just deleted it.

       [http://www.cgsecurity.org/wiki/TestDisk](http://www.cgsecurity.org/wiki/TestDisk)

 Testdisk Instructions
[http://www.cgsecurity.org/wiki/TestDisk_Step_By_Step](http://www.cgsecurity.org/wiki/TestDisk_Step_By_Step)
[http://www.cgsecurity.org/wiki/Menu_Analyse](http://www.cgsecurity.org/wiki/Menu_Analyse)

Testdisk shows all versions of old partitions, you have to select the combination that matches.
You would want to include all your existing partitions and one more logical that starts just after end of sda5 778011947 and ends just before end of extended partition sda2 at 972580863 or just before the start of sda3. But testdisk uses the CHS not sectors and probably does not show extended. Just all logical partitions sda5 & sda6 must be in one extended partition.

If partition is recreated it probably gets a new UUID and you will still have to update grub.
Either Boot-Repair or manually reinstall grub.

       How to restore the Ubuntu/XP/Vista/7 bootloader 
[https://help.ubuntu.com/community/RestoreUbuntu/XP/Vista/7Bootloader](https://help.ubuntu.com/community/RestoreUbuntu/XP/Vista/7Bootloader)
[https://help.ubuntu.com/community/Grub2/Installing#Fixing_a_Broken_System](https://help.ubuntu.com/community/Grub2/Installing#Fixing_a_Broken_System)

---

### Post by broaff on 2014-06-08
Thanks for the fast response! It's working, i successfully restored the original win boot manager. If i have enough spiritual power, i will make a new grub, but for now this is enough for me.

Cheers

---

### Post by oldfred on 2014-06-08
It also looks like your HPtools is now a logical partition. That is often what is a recommendation around the 4 primary partition limit, so that is not an issue.
If you do recover Linux partitions / & swap they then will not be the same sda5 & sda6 and will have new UUIDs. Or you have to reinstall grub2 and edit fstab with new UUIDs. Or if no data to worry about just reinstall into the unallocated space.

---

