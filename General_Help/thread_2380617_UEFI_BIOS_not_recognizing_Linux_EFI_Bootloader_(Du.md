---
title: "UEFI BIOS not recognizing Linux EFI Bootloader (Dual Boot)"
date: 2017-12-19
forum: General Help
---

### Post by ubuntini2 on 2017-12-19
First a quick background
I had a working dual boot(not technically dual boot since I was using 2 hard drives) Linux(Ubuntu) and Windows 10 setup.

Windows was booting on a M.2 512GB SSD and Ubuntu Linux was on a 2nd Samsung 950 Pro SSD.
I could easilly switch between the 2 thru the UEFI/BIOS.

I upgraded to a new motherboard + CPU (AMD Threadripper + Asus ROG Zenith Extreme) and simply transferred the 2 SSD's over to the new mobo.

When I boot I immediately go into WIndows 10 without issue.
In the UEFI BIOS even if I select the Ubuntu disk option it ignores that and still boots into Windows. (see attached)

I have disabled both Secure and Fast boot in UEFI/BIOS.

It seems as though the UEFI/BIOS is simply not recognizing the existing Linux EFI bootloader.

Any dual boot experts able to suggest what I might try next?

I'm hoping I don't have to repartition and reinstall Ubuntu from scratch!

[ATTACH=CONFIG]277885[/ATTACH]

---

### Post by yancek on 2017-12-19
What happens when you set the Samsung 950 Pro SSD option, the drive on which you have Ubuntu.  Same failure?  Which drive had the EFI partition, the windows?  You might try going to the site below and downloading and running boot repair to get more info to post here.  Use the 2nd option to download from the ppa using your Ubuntu install media and when you run boot repair, make sure you do NOT try to make any repairs but select the option to Create BootInfo Summary.  THis will output a link you can post here and members familiar with UEFI might be able to help.

[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)

---

### Post by ubuntini2 on 2017-12-19
Thanks for the quick reply!
Here is the system report from Boot repair (though it didn't help)

[https://paste.ubuntu.com/26217723/](https://paste.ubuntu.com/26217723/)

---

### Post by yancek on 2017-12-19
> Here is the system report from Boot repair (though it didn't help)

No, nor was it supposed to as the only purpose was to gather information.  In the image from your original post you showed several options which included Ubuntu, windows and the SSD drive on which you have Ubuntu.  When you select the SSD drive option, do you get the same results?

Your boot repair output doesn't show any info on the various SSD partitions for some reason although both the windows and Ubuntu SSD's are recognized.  More details show for the windows SSD than the UBuntu SSD for some reason.

There is no grub.cfg file on the Ubuntu drive showing, only the one from the flash drive you are using.  In the boot repair you see the line below which means it is not finding your Ubuntu Linux.

> 1 disks with OS, 1 OS : 0 Linux, 0 MacOS, 1 Windows, 0 unknown type OS. 

Near the bottom of the output, you can see some details on partitions on the windows SSD but none for the Ubuntu, not sure why that is.  If you can try the SSD 950 option in the BIOS and that fails, I'm not sure what else to try.  I don't use SSD's so I'm really not sure what can be done.

---

### Post by oldfred on 2017-12-19
Many with Samsung SSD have had to update firmware. Have you tried that?

But Samsung details are not shown only the NVMe device?
nvme2n1   disk             477G
nvme1n1   disk             477G

the UEFI boot entry in UEFI shows a different GUID, so did you have a separte ESP - efi system partition on the Samsung?

---

### Post by ubuntini2 on 2017-12-19
Thanks.
has been about a year since I set up my old dual boot system so I need to refresh my memory.

There are also 2 blank NvMe M.2 drives (I am hoping to set up as a RAID 0 array)which may be part of the confusion

This is more or less an exhaustive description of what I originally did. Apologies for the length!

> 
Follow the following 2 SSD Windows -Linux install guide EXCEPT FOR
format-partitioning (better to preformat-partition using gParted)  and
disabling CSM (leave it Enabled)

gParted partitioning for 1TB SSD(also attached)
1 ESP 550 MiB
2 root 40GB (4096 MiB)
3 home 640 GB (655,360 MiB
4 swap 128 GB (131,072) MiB
remainder unallocated

This should work for most systems that use UEFI and which have two HDD.


A) UEFI/BIOS &#8211; 1) Set to UEFI mode only (no legacy/CSM). 2) Disable
secure boot 3) Disable Intel Rapid Start (if equipped) 3) Disable fast
boot in UEFI (note this is different than the &#8220;fastboot&#8221; setting in
Windows 8/10). The options in your UEFI/BIOS might say something like
Full/Minimal/Automatic for boot mode. Select Full (or thorough, or
complete, etc whatever your UEFI vendor has chosen to call it).

B) Disable fastboot in Windows 8/10 under advanced power options.
Restart computer to ensure that this subsequent boot and the next
reboot/shutdown will be in &#8220;normal&#8221; mode.

B1) Optional &#8211; Install Macrium Reflect (free) and create a backup image
and reinstallation media should something go wrong with Windows 10.

C) Use Rufus to create a bootable USB stick with your choice of Ubuntu
based distro. Make sure in Rufus that you CHOOSE the option UEFI/GPT
only. This ensures the Linux environment boots only into UEFI mode
during your install.

D) Reboot computer and press key for one time boot menu (Dell is
typically F12). Selected your USB stick from the boot options &#8211; note
make sure it says UEFI in front of the USB stick in the boot menu. If
not, return to Windows and recreate your USB stick with Rufus ensuring
you choose the UEFI/GPT (only) option.

E) Boot into Linux live environment and begin install.

F) When you get to the installation option, choose SOMETHING ELSE at the
bottom of the Ubiquity installer.

G) Find your secondary HDD that you will be installing Linux to. In my
case it was listed as /dev/sdc (with /dev/sda being the windows drive
and /dev/sdb the USB drive [which was invisible in the installer]).
Partition the target drive as follows:
-select Make New Partition Table
-1st partition, 650MB size, EFI as the type (this will list as /dev/sdb1
efi in the partitioning tool once you create it)
-2nd partition, 10GB min (20+GB better), mountpoint is root (/) ext4 as
file system
-3rd partition, 2GB min, swap, (if you wish to use hibernation, the swap
needs to be just slightly larger than your total amount of RAM &#8211; example
I have 8GB so the size of this parition was set at 9000MB)
-4th partition, remainder of space on drive, mountpoint home (/home),
ext4 as file system

[B]******
[/B]IMPORTANT
[B]******
[/B]F) BEFORE clicking &#8220;Install Now&#8221;, from the &#8220;device for boot loader
installation&#8221; option button, select the 650MB EFI partition you just
created as the target for the bootloader. (example /dev/sdc1 in my
case). Then click &#8220;Install Now&#8221;.

G) Finish installation process. And reboot (removing the USB stick when
your UEFI/BIOS screen logo appears).

Upon reboot, after UEFI/BIOS reads the new bootloader entry that Linux
has added to it, you will be presented with the grub menu with a listing
of your Linux distro as well as a listing to boot Windows 10. Boot into
Linux. Install any updates and then reboot and attempt to enter Windows
10 from the grub menu to make sure that grub correctly handles the
hand-off to the Windows 10 bootloader.

WHAT YOU HAVE DONE. You have installed the Linux EFI bootloader to the
newly created EFI partition. In the process of this, Linux has added an
entry to your UEFI listings in your systems UEFI/BIOS. Linux has also
automatically detected your Windows 10 install and added a grub menu
item to boot it. Your computer at this point will now automatically boot
to Linux unless you choose to boot to Windows (from the Grub menu).

What you haven&#8217;t done. You haven&#8217;t in any way altered your Windows 10
install or its bootloader or even so much as touched the Windows 10 EFI
partition. Everything is reversible simply by removing the Linux UEFI
listing from your UEFI/BIOS settings. How to do so varies from each
vendor.

---

### Post by ubuntini2 on 2017-12-19
Update
Wondering if my Samsung 850 EVO SSD with Linux partition is even mounted?


If I do a wmic logicaldisk get size,freespace,caption
I only see my C and D partitions for my boot M.2 SSD
C:       131529646080  209202888704
D:       288785301504  301801140224


Also under Device manager under Disk Drives, I only see 1 listing. (I should see 2)
NVMe Samsung SSD 950 SCSI Disk Device (my boot M.2 SSD)

Also downloaded and ran latest Samsung SSD Magician software, and it only sees my boot M.2 SSD.

---

### Post by oldfred on 2017-12-19
Did you turn on RAID in UEFI? It needs to be AHCI.
If you want RAID, better to install server version and add in desktop of your choice.
Is drive shown correctly in UEFI drive listing?

       Don't bother with RAID 0 unless you have a specific need for speed without data redundancy, since if one drive goes out, you lose the whole array.
[http://en.wikipedia.org/wiki/RAID](http://en.wikipedia.org/wiki/RAID)
[http://www.smallnetbuilder.com/nas/nas-features/31745-data-recovery-tales-raid-is-not-backup](http://www.smallnetbuilder.com/nas/nas-features/31745-data-recovery-tales-raid-is-not-backup)

I think your NVMe drive is faster than most RAID systems. So not sure how much more speed you get with RAID.

---

### Post by ubuntini2 on 2017-12-20
Bingo! Yes that was the issue


Thanks for the feedback. Have to admit my dumb mistake!
In anticipation of configuring 2 additional NVMe drives as RAID had changes my SATA setting in BIOS to RAID.


Switched back to AHCI, rebooted with Boot Repair, reinstalled grub and was good to go.

---

