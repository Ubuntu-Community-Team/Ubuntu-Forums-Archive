---
title: "Windows 7 tries to repair my ext4 partition and corrupts it"
date: 2015-10-08
forum: General Help
---

### Post by m4gaikwad on 2015-10-08
Some days ago I accidentally formatted my Ext4 partition to NTFS. But recovered it by backup super block. After that my Windows 7 started repairing the ext4 partition considering it as NTFS. I checked the partition id of ext4 it says 83 and Linux. But still Windows 7 harasses me with continuously asking me to repair the drive . I hate Windows but its for work. Please does anybody have solution for it?

Thanks in Advance.

---

### Post by oldfred on 2015-10-08
I do not know how to easily see partition boot sector (PBR) except with Boot-Repair's summary report. (testdisk or dd will show it, but not easy or recommeded) Windows looks at PBR more than partition table. You may still have a NTFS signature in PBR.

       Post the link to the Create BootInfo summary report. Is part of Boot-Repair:
[https://help.ubuntu.com/community/Boot-Info](https://help.ubuntu.com/community/Boot-Info)

---

### Post by m4gaikwad on 2015-10-08
[http://paste.ubuntu.com/12716906/](http://paste.ubuntu.com/12716906/)


Well this is my Boot-Repair Summary report. It shows the current ext4 partition in Boot Sector Type as Windows 8 /2012 NTFS. Is there any way to resolve it??

Thanks in Advance

---

### Post by oldfred on 2015-10-08
Not related, but you need to move boot flag back to sda1. Windows need to use boot flag to know which NTFS partition is bootable, or to repair.
Grub does not use boot flag. It finds its own boot partitions and searches for Windows boot files to know if there is a Windows boot partition to chainload to.

Found my notes on directly printing partition boot sector.
sudo dd if=/dev/sda3 bs=1 count=512 | hexdump -C

I think we can zero out the first few bytes so it does not show as valid NTFS. But we have to be careful not to zero out too much. 
Does testdisk show a backup partition entry. Normally used to restore a damaged NTFS boot sector, but perhaps backup is invalid and we can restore it?
       [http://www.cgsecurity.org/wiki/TestDisk_Step_By_Step#NTFS_Boot_sector_recovery](http://www.cgsecurity.org/wiki/TestDisk_Step_By_Step#NTFS_Boot_sector_recovery)

---

### Post by m4gaikwad on 2015-10-09
I tried Testdisk at first when I accidentally formated ext4 to ntfs but backup partition entry was invalid.So used super block backup. It saved the day.I have attached my hexdump.
[ATTACH]264867[/ATTACH]

---

### Post by oldfred on 2015-10-09
I think at least part of issue is the NTFS at beginning.
Partition boot sector - PBR is identical in construction to MBR.
I we should be able to erase the code area, but not change the partition area, which in PBR may not be used except in extended & logical partitions.

Be sure you have good backups.

I have never done this so lets back PBR up first.
sudo dd if=/dev/sda3 of=pbr_sda3.bin bs=512 count=1
The zero out code part or first 446.

 sudo dd if=/dev/zero of=/dev/sda3 bs=446 count=1

Make absolutely sure that you have correct partition and if & of entries. If any error with dd, if just about is not recoverable. DD nickname is data destroyer.

---

### Post by m4gaikwad on 2015-10-09
I changed boot flag from linux partition to Windows . It really worked. So didnt try zeroing out the bytes maybe later . oldfred Thanks for helping out.

---

