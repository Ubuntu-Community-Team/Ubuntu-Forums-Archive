---
title: "Remove windows boot loader from grub menu"
date: 2016-01-02
forum: General Help
---

### Post by philk949 on 2016-01-02
I've just removed Windows 8 from a dual boot system and extended my Ubuntu Mate 15.1 to take up the space vacated. However, when I boot there is still an entry for Windows Boot Loader in the GRUB menu. How do I uninstall this entry and can I boot without having to go through GRUB afterwards? Thank you in advance.

---

### Post by westie457 on 2016-01-02
Hi, the usual way to remove entries from grub is ```
sudo update-grub
```

If that does not work there are other ways. One is to use 'BootRepair' the other is to manually purge and reinstall grub.

Boot repair is here. [https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)

The manual method is here. [http://ubuntuforums.org/showthread.php?t=1581099](http://ubuntuforums.org/showthread.php?t=1581099)

---

### Post by philk949 on 2016-01-02
Thanks Westie, I'll give this a shot and get back to you.

---

### Post by philk949 on 2016-01-02
None of the options worked and I now have multiple entries in the GRUB menu that weren't there before, most of which I don't understand.
The pastebin URL from the boot repair option is as follows: [http://paste.ubuntu.com/14380016](http://paste.ubuntu.com/14380016)

---

### Post by Bucky Ball on 2016-01-02
Looks like you have Windows 8 installed twice:

```
sda6: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows 8/2012: NTFS
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        

sda7: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows 8/2012: NTFS
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:    
```

And hello from sunny Adelaide. :)

---

### Post by philk949 on 2016-01-02
Looks that way doesn't it, but there is no Windows OS on the disc. When I was trying the repair options I recall a notification that the boot files for Ubuntu were not at the very start of the disc so would going into Gparted be an option to see what I can do from there?

---

### Post by Bucky Ball on 2016-01-02
Going to gparted, deleting your two Windows partitions (after backing up any valuable data from them), then 'sudo update-grub' would probably be a place to start. 

If your bootinfo is showing you have two NTFS partitions there, they are there.

---

### Post by philk949 on 2016-01-02
OK Bucky, I'll get back to you. And thanks.

---

### Post by philk949 on 2016-01-02
Deleted one ntfs partition at start of disc but here is what I get at boot now:

Ubuntu
Advanced options for Ubuntu
Windows UEFI Recovery bootmgfw.efi
Windows boot UEFI recovery
EFI / ubuntu/Mokmanager.efi
Windows UEFI Recovery LrsBootmgr.efi
Windows boot UEFI recovery bkpbootx64.efi
Windows Boot Manager (on /dev/sda2)
System setup

Should I go back in and delete anything with an ntfs file system?

---

### Post by Bucky Ball on 2016-01-03
Hmm. As this is EFI install it may require you to remove entries from the EFI boot partition. I know nothing about doing this so hopefully someone who does will leap in shortly. :)

You have two EFI boot partitions for some reason, sda2 and sda3, so don't touch either or you might not be able to boot anything. 

sda6 and sda7 can go, though. They look like regular NTFS partitions. 

When you say you 'deleted one of the partitions', please be specific. We need to know exactly what you are doing so we can work out how the drive is looking by comparing with your bootinfo. You could get into hot water if you delete partitions without knowing the consequences. ;)

I'm presuming you killed sda6 or 7?

PS: You need to update grub after you kill a windows install. Incidentally, you don't seem to have an entry there to actually boot Win, just a whole lot of recovery entries. This is why I'm wondering if they need to be removed from the UEFI partition. :-k

---

### Post by westie457 on 2016-01-03
This might help with the removal of Windows OS partitions including the recovery partitons and removing the entries from 'nvram'

[https://help.ubuntu.com/community/OS-Uninstaller](https://help.ubuntu.com/community/OS-Uninstaller)

If you already have BootRepair installed OS-Uninstaller is available in 'Synaptic' or 'Software Centre'

At the time of writing this I have not tried OS-Uninstaller so cannot say for definite that it works.

I have read somewhere that changing the HDD removes entries also. Changing the drive in some Lenovo laptops is not an easy task, in fact it is very nearly a complete dismantle and re-build.

Some information if you are not already aware.

The Lenovo One-Key Recovery will not work at all if you want to reinstall Windows. The OKR stops working when the size of any partition changes. 
It is possible to rebuild the OKR. The procedure (if you want it) is available in the Lenovo Forums. [https://forums.lenovo.com/t5/Lenovo-Yoga-Series-Notebooks/Solved-Fix-Repair-Nova-Button-One-Key-Recovery-after-replacing/m-p/1829369/highlight/true#M26820](https://forums.lenovo.com/t5/Lenovo-Yoga-Series-Notebooks/Solved-Fix-Repair-Nova-Button-One-Key-Recovery-after-replacing/m-p/1829369/highlight/true#M26820)

---

### Post by oldfred on 2016-01-03
With UEFI, you have to remove the folders in the ESP - efi system partition first (or UEFI may add them back) and separately remove the entries from UEFI as it has NVRAM and saves entries.

It looks like sda3 was a hidden efi partition with boot files for vendor system recovery. Your ESP is sda2. Best to fully back up Windows, Windows recovery, and efi partition(s) before deleting. Many users come back and have one application or game that does not run in Linux and wants Windows back or wants to sell system and needs to restore Windows. 

So you should be able to go into /boot/efi/EFI and delete the Microsoft folder.

Then use efibootmgr to remove Windows entry from UEFI. Boot-Repair showed it as 0003, but confirm first:
       Check entry is there.
sudo efibootmgr -v 

            Delete entry change XXXX to correct entries. Some UEFI require all 4 HEX char, other just need 1 or 2 significant char.
sudo efibootmgr -b XXXX -B

            The "-v" option displays all the entries so you can confirm you're deleting the right one, and then you use the combination of "-b ####" (to specify the entry) and "-B" (to delete it). Examples #5 is delete:, with Ubuntu you need sudo, others must be at root.
efibootmgr -b XXXX -B
[http://linux.die.net/man/8/efibootmgr](http://linux.die.net/man/8/efibootmgr)
[http://linux.dell.com/cgi-bin/gitweb/gitweb.cgi?p=efibootmgr.git;a=blob_plain;f=README;hb=HEAD](http://linux.dell.com/cgi-bin/gitweb/gitweb.cgi?p=efibootmgr.git;a=blob_plain;f=README;hb=HEAD)

---

