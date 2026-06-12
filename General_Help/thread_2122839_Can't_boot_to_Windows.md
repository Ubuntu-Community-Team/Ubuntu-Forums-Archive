---
title: "Can't boot to Windows"
date: 2013-03-06
forum: General Help
---

### Post by Lolanerd on 2013-03-06
I finally got around to dual booting ubuntu 12.10 on my lenovo ideapad y580 yesterday and allocated about 350 gb to each partition (windows 8 and ubuntu). However, my windows 8 is installed in the 16 gb ssd that came with my laptop, and for some reason I'm not able to boot into it from ubuntu's boot menu. Anyone know what up? Any help would be appreciated, thanks.

---

### Post by Bradley129 on 2013-03-06
Im new here so bare with me im trying to help but have you tried sudo update-grub ?

---

### Post by cortman on 2013-03-06
Try Bradley129's suggestion, and if that doesn't work, post back the output of

```
sudo fdisk -l
```

---

### Post by oldfred on 2013-03-06
You mention small SSD. Is this an UltraBook or Intel SRT is the standard used by all vendors for UltraBooks.

  Intel Smart Response Technology
[http://www.intel.com/p/en_US/support/highlights/chpsts/imsm](http://www.intel.com/p/en_US/support/highlights/chpsts/imsm)
Some general info in post #3
[http://ubuntuforums.org/showthread.php?t=2071242](http://ubuntuforums.org/showthread.php?t=2071242)

      
 Intel SRT - Dell XPS Screen shots of Intel SRT screens & lots of details 
[http://ubuntuforums.org/showthread.php?t=2038121](http://ubuntuforums.org/showthread.php?t=2038121)
[http://ubuntuforums.org/showthread.php?t=2036204](http://ubuntuforums.org/showthread.php?t=2036204)
Details in post #10 on an install that worked
[URL="http://ubuntuforums.org/showthread.php?t=2020155"]http://ubuntuforums.org/showthread.php?t=2020155

      [/URL]
 Some info on re-instating  details in post #9
[http://ubuntuforums.org/showthread.php?t=2038121](http://ubuntuforums.org/showthread.php?t=2038121)
[http://ubuntuforums.org/showthread.php?t=2070491](http://ubuntuforums.org/showthread.php?t=2070491)
> Disable the RAID, for me it was using the Intel rapid management thingy and telling it to disable the acceleration or the use of the SSD. If you have a different system, just disable the RAID system then install Ubuntu. Once installed you can then re-enable it.
sudo dmraid -E -r /dev/sda
sudo dmraid -E -r /dev/sdb
> You will need to use the dmraid command prior to running the Ubuntu Installer so that it will be able to see the partitions on the drive because otherwise with the raid metadata in place it will see the drive as part of a raid set and ignore its partitions.

    [URL="http://ubuntuforums.org/showthread.php?t=2020155"]
[/URL]

---

### Post by Lolanerd on 2013-03-06
Sorry for the late reply guys, I have terrible connection at school. Do I have to have root privileges to run sudo commands? Because they don't seem to do anything as far as I can tell.

Edit: Sorry, I was using the wrong app on accident lol. The output of sudo fdisk -l was:

WARNING: GPT (GUID Partition Table) detected on '/dev/sda'! The util fdisk doesn't support GPT. Use GNU Parted.


Disk /dev/sda: 16.0 GB, 16013942784 bytes
256 heads, 63 sectors/track, 1939 cylinders, total 31277232 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0xf79d9f0d

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1  4294967295  2147483647+  ee  GPT

WARNING: GPT (GUID Partition Table) detected on '/dev/sdb'! The util fdisk doesn't support GPT. Use GNU Parted.


Disk /dev/sdb: 750.2 GB, 750156374016 bytes
255 heads, 63 sectors/track, 91201 cylinders, total 1465149168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes
Disk identifier: 0xf79d9f00

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1  1465149167   732574583+  ee  GPT
Partition 1 does not start on physical sector boundary.

---

### Post by Lolanerd on 2013-03-06
> **oldfred said:**
> You mention small SSD. Is this an UltraBook or Intel SRT is the standard used by all vendors for UltraBooks.

  Intel Smart Response Technology
[http://www.intel.com/p/en_US/support/highlights/chpsts/imsm](http://www.intel.com/p/en_US/support/highlights/chpsts/imsm)
Some general info in post #3
[http://ubuntuforums.org/showthread.php?t=2071242](http://ubuntuforums.org/showthread.php?t=2071242)

      
 Intel SRT - Dell XPS Screen shots of Intel SRT screens & lots of details 
[http://ubuntuforums.org/showthread.php?t=2038121](http://ubuntuforums.org/showthread.php?t=2038121)
[http://ubuntuforums.org/showthread.php?t=2036204](http://ubuntuforums.org/showthread.php?t=2036204)
Details in post #10 on an install that worked
[URL="http://ubuntuforums.org/showthread.php?t=2020155"]http://ubuntuforums.org/showthread.php?t=2020155

      [/URL]
 Some info on re-instating  details in post #9
[http://ubuntuforums.org/showthread.php?t=2038121](http://ubuntuforums.org/showthread.php?t=2038121)
[http://ubuntuforums.org/showthread.php?t=2070491](http://ubuntuforums.org/showthread.php?t=2070491)

No, it isn't an ultrabook. If I use the method detailed in post #9 of the last link, do I have to uninstall(?) ubuntu then reinstall it?

---

### Post by oldfred on 2013-03-07
Did you install Ubuntu in BIOS/CHM mode? It should be in UEFI mode?

Boot Repair can convert a BIOS install to UEFI, since you have gpt partitioning.

       Post the link to the BootInfo report that this creates. Is part of Boot-Repair:
[https://help.ubuntu.com/community/Boot-Info](https://help.ubuntu.com/community/Boot-Info)
Boot Repair -Also handles LVM, GPT, separate /boot and UEFI dual boot.:
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)
You can repair many boot issues with this or 'Create BootInfo' report (Other Options) & post the link it creates, so we can see your exact configuration and diagnose advanced problems.
Install in Ubuntu liveCD or USB or Full RepairCD with Boot-Repair (for newer computers) 
[http://sourceforge.net/p/boot-repair/home/Home/](http://sourceforge.net/p/boot-repair/home/Home/)
[https://help.ubuntu.com/community/UbuntuSecureRemix](https://help.ubuntu.com/community/UbuntuSecureRemix)
    
 How Boot-Repair fixes a Ubuntu with grub-pc with efi Windows
[http://ubuntuforums.org/showpost.php?p=12205679&postcount=516](http://ubuntuforums.org/showpost.php?p=12205679&postcount=516)
Boot-Repair - Updated Jan 1, 2013 to not rename first time, but rename if first time Windows does not boot. Post 706 and 711
[http://ubuntuforums.org/showthread.php?t=1769482&page=71](http://ubuntuforums.org/showthread.php?t=1769482&page=71)
 Boot-Repair copied /EFI/ubuntu/grubx64.efi to /EFI/Boot/bootx64.efi (in case the BIOS is hard-coded to boot into /EFI/Boot/bootx64.efi or secure boot
signed GRUB file shimx64.efi.

Others with similar systems

 Lenovo Z580 laptop
[http://ubuntuforums.org/showthread.php?t=2112271](http://ubuntuforums.org/showthread.php?t=2112271)
[http://ubuntuforums.org/showthread.php?t=2117760](http://ubuntuforums.org/showthread.php?t=2117760)
Lenovo Ideapad Y500 LiveUSB Problem
[http://ubuntuforums.org/showthread.php?t=2095063](http://ubuntuforums.org/showthread.php?t=2095063)

---

### Post by Lolanerd on 2013-03-07
Here's the link: 
[Http://Paste.ubuntu.com/5593381/](Http://Paste.ubuntu.com/5593381/)

Also, I was able to boot in to Windows by going to that last option on grub and moving the order of windows boot manager up above ubuntu. But it still doesn't show up on the grub list.

---

### Post by oldfred on 2013-03-07
Usually Boot-Repair adds correct efi boot entries.
You can manually add entries as shown as work arounds in this bug report.
 grub2's os-prober creates wrong style (BIOS) chain boot entry
[https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/1024383](https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/1024383)
type of entry from Boot-Repair that should work.
'Windows UEFI loader'
Type of entry that does not work:
'Windows ...) (on /dev/sdXY)'

You may have to add this for Ubuntu to see Windows as you have Intel SRT.
sudo apt-get install mdadm
      
Intel Smart Response Technology
[http://www.intel.com/p/en_US/support/highlights/chpsts/imsm](http://www.intel.com/p/en_US/support/highlights/chpsts/imsm)
Some general info in post #3
[http://ubuntuforums.org/showthread.php?t=2071242](http://ubuntuforums.org/showthread.php?t=2071242)

 Some info on re-instating  details in post #9
[http://ubuntuforums.org/showthread.php?t=2038121](http://ubuntuforums.org/showthread.php?t=2038121)
[http://ubuntuforums.org/showthread.php?t=2070491](http://ubuntuforums.org/showthread.php?t=2070491)

---

### Post by Lolanerd on 2013-03-07
Ok so I ran the recommended boot repair. Here's the log: http://paste.ubuntu.com/5594562/

There's a bunch of windows options on grub now, but none of them work. The only way I can boot to windows is if I go to the boot section from the system settings and set the order of windows above that of ubuntu.

---

### Post by oldfred on 2013-03-07
Both of these entries should work. Not sure why they think it is recovery.

 menuentry "Windows UEFI recovery bootmgfw.efi" {
search --fs-uuid --no-floppy --set=root [COLOR=#ff0000]6CFD-C181[/COLOR]
chainloader (${root})/EFI/Microsoft/Boot/bootmgfw.efi
}

   menuentry "Windows Boot UEFI recovery" {
search --fs-uuid --no-floppy --set=root [COLOR=#ff0000]6CFD-C181[/COLOR]
chainloader (${root})/EFI/Boot/bootx64.efi
}

[COLOR=#ff0000]6CFD-C181[/COLOR] is the UUID of your efi partition. The other are to the real recovery partition or incorrect one's from grub2's os-prober.

---

### Post by Lolanerd on 2013-03-07
Yeah, I read the link you posted and those 2 should work, but it says image not found or something like that. Any ideas on something else I can try? Also, would reinstalling be a good idea? 
On that note, do I have to uninstall ubuntu before I can reinstall it? If so, how would I uninstall? 
Thanks for all the help oldfred

---

### Post by oldfred on 2013-03-07
If you use Something Else and choose the same / (root) partition as you now have, same /home (but do not reformat) that will reinstall and save any user customization and data you have. But you should not have to.

There really should not be any difference in booting Windows from UEFI menu or from grub chain loading back to the same efi file to boot Windows. Windows boots ok from UEFI menu.

Is secure boot on or off? Some only work with secure boot off.

---

### Post by Lolanerd on 2013-03-07
I think it's on, I'll try it with secure boot off I guess and report back.

---

### Post by Lolanerd on 2013-03-07
> **oldfred said:**
> If you use Something Else and choose the same / (root) partition as you now have, same /home (but do not reformat) that will reinstall and save any user customization and data you have. But you should not have to.

There really should not be any difference in booting Windows from UEFI menu or from grub chain loading back to the same efi file to boot Windows. Windows boots ok from UEFI menu.

Is secure boot on or off? Some only work with secure boot off.

> **Lolanerd said:**
> I think it's on, I'll try it with secure boot off I guess and report back.

Yeah, turning off secure boot worked. Everything seems to be running fine now. Thank you so much for all the help :D

---

### Post by oldfred on 2013-03-08
Glad that worked. :)

Some systems boot only with secure boot off. Others will boot with it on or off. Since Ubuntu has the Microsoft key, it is the vendors version of UEFI that needs updating, so if they have an update to UEFI/BIOS later on, then it may work.

---

