---
title: "Can't Boot Windows After 12.10 Install"
date: 2012-10-30
forum: General Help
---

### Post by ace214 on 2012-10-30
Ran a boot repair, and now Windows shows up in GRUB but when I try to boot to it, I just get a flashing cursor.

Here's my boot-info: [http://paste.ubuntu.com/1318864/]("http://paste.ubuntu.com/1318864/")

Thanks in advance!

---

### Post by COMECON on 2012-10-30
Hi!
I had an issue like that, and after searching a lot, I added this to **/etc/grub.d/40_custom**:
```

menuentry "Windows 7 (boot) (on /dev/sda5)" --class windows --class os {
    insmod part_msdos
    insmod ntfs
    insmod ntldr
    set root='(hd0,msdos5)'
    search --no-floppy --fs-uuid --set=root 1EA0019AA0017A13
    ntldr ($root)/bootmgr
}

```

After editing that file (*gksudo /etc/grub.d/40_custom*) just run:
```
$ sudo update-grub
```

Then restart, and you should see a new entry on the bottom of the list. At least it worked for me, though I see a warning when I boot on Windows, but it works great :)

---

### Post by ace214 on 2012-10-30
> **COMECON said:**
> Hi!
I had an issue like that, and after searching a lot, I added this to **/etc/grub.d/40_custom**:
```

menuentry "Windows 7 (boot) (on /dev/sda5)" --class windows --class os {
    insmod part_msdos
    insmod ntfs
    insmod ntldr
    set root='(hd0,msdos5)'
    search --no-floppy --fs-uuid --set=root 1EA0019AA0017A13
    ntldr ($root)/bootmgr
}

```

After editing that file (*gksudo /etc/grub.d/40_custom*) just run:
```
$ sudo update-grub
```

Then restart, and you should see a new entry on the bottom of the list. At least it worked for me, though I see a warning when I boot on Windows, but it works great :)


Unfortunately, that didn't do it. I had to change the blockID, but then I get a message about bootmgr not existing.

Forgot to mention that the Windows version is XP.

---

### Post by Mark Phelps on 2012-10-30
According to the info you posted, the boot flag for the sda disk partitions is on a Linux partition.  If sda5 really is your XP boot partition, it needs to have the boot flag on it.

Otherwise, could sdb1 be your XP boot partition?

Look for the partition containing the NTLDR file -- that is your XP boot partition -- and set it to have the boot flag.

You can do this using GParted.

---

### Post by ace214 on 2012-10-31
> **Mark Phelps said:**
> According to the info you posted, the boot flag for the sda disk partitions is on a Linux partition.  If sda5 really is your XP boot partition, it needs to have the boot flag on it.

Otherwise, could sdb1 be your XP boot partition?

Look for the partition containing the NTLDR file -- that is your XP boot partition -- and set it to have the boot flag.

You can do this using GParted.

Unfortunately, that didn't work either... Curiously, when I ran boot repair after changing the boot flag, it changed it back- making my Linux partition have the boot flag.

New boot info: [http://paste.ubuntu.com/1320922/]("http://paste.ubuntu.com/1320922/")

---

### Post by oldfred on 2012-10-31
Offically Windows does not boot from a logical partition. It will only boot from a primary (sda1 thru sda4)  NTFS formated partition with the boot flag.

 ```
sda5: ____________________________________

    File system:       ntfs
    Boot sector type:  Windows XP: NTFS
    Boot sector info:  According to the info in the boot sector, [COLOR=Red]sda5[/COLOR] starts 
                       at [COLOR=Red]sector 63[/COLOR].
    Operating System:  Windows XP
    Boot files:        /boot.ini /ntldr /NTDETECT.COM
```You somehow moved your Windows from sda1 to sda5 and it is the only partition inside your extended partition.

Two choices. 

Only with XP there are work arounds to make Windows boot from a logical. 

But you only used 3 partitions, so you can convert sda5 back to sda1 and still have a primary for future use as an extended to make additonal logical partitons if desired.

Fixparts has options to convert primary & logical. You have to follow all the partition rules so only some options are available, but you should be able to convert sda5 back to primary.

First backup partition table
sudo sfdisk -d /dev/sda > parts_sda.txt

Fixparts - Repair broken partition tables (not overlapping issues) & delete Stray gpt data from MBR drives
[http://ubuntuforums.org/showthread.php?t=1705325](http://ubuntuforums.org/showthread.php?t=1705325) 
[http://www.rodsbooks.com/fixparts/](http://www.rodsbooks.com/fixparts/)

 backup partition table, use your drive for sdX or sda, sdb etc.
sudo sfdisk -d /dev/sdX > parts.txt

You may need to run chkdsk from a Windows XP CD to make sure the XP partition is ok. And remote possibility of other changes may need grub2  reinstalled so have a current Ubuntu liveCD.

---

### Post by ace214 on 2012-10-31
Well, that was helpful in getting the drive better partitioned, but it didn't fix the problem.

I think it's probably a Windows issue. I used the Windows recovery console and did a "fixboot" and "fixmbr" and it now gives me the same flashing cursor I got through GRUB...

---

### Post by oldfred on 2012-10-31
Did you run chkdsk. And run it until there is no error? Tha tshould also fix boot partition. I think sometimes fixboot just restores the backup PBR and the backup may not be any better.

Some also reinstall ntldr, NTDETECT.COM, and redo boot.ini to make sure boot files are ok.

Testdisk can also build a new PBR or Boot Sector. It is only an XP version but that is what you want.
If Microsoft's Checkdisk (chkdsk) failed to repair the MFT, run TestDisk, also rebuild boot sector
[http://www.cgsecurity.org/wiki/Advanced_NTFS_Boot_and_MFT_Repair](http://www.cgsecurity.org/wiki/Advanced_NTFS_Boot_and_MFT_Repair)

One user had a MFT that overlapped BS. He could fix one or the other but never could totally repair it.
But sometimes too much moving about of the NTFS partition just causes too many issues.

---

### Post by ace214 on 2012-10-31
> **oldfred said:**
> Testdisk can also build a new PBR or Boot Sector. It is only an XP version but that is what you want.
If Microsoft's Checkdisk (chkdsk) failed to repair the MFT, run TestDisk, also rebuild boot sector
[http://www.cgsecurity.org/wiki/Advanced_NTFS_Boot_and_MFT_Repair](http://www.cgsecurity.org/wiki/Advanced_NTFS_Boot_and_MFT_Repair)

Thank you!! That did it!

---

