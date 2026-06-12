---
title: "SSD in new device: will not boot, boot repair fails"
date: 2017-01-18
forum: General Help
---

### Post by jamespetts on 2017-01-18
I had a small NUC that I use to take to work, an Intel Skylake i5. On Saturday, it suddenly failed totally (would not power on). Happily, it was within warranty, so I returned it to Amazon and a new one arrived. (Actually, Amazon have not collected the old one from my workplace yet, but that is another matter). 

I had bought it as a barebones system, so I had my own RAM and M.2 SSD, which I took out of the old one before returning it. I collected the replacement to-day, and installed my RAM and SSD. The hardware seems to work, but I cannot get it to boot from the SSD. I have managed to get it to boot with an Ubuntu 16.04 ISO installed on a USB drive, and it appears to work correctly. I can see the SSD and the various partitions on it.

I had encrypted the SSD using whole device encryption. I remember my passphrase, and was able to unlock when I booted from the USB drive. However, I cannot find any way of making it bootable from the SSD any longer. When I try to boot, the BIOS simply tells me that there are no bootable drives. I have tried:

(1) updating the BIOS to version 54;
(2) checking many different settings in the BIOS and boot menu to see whether it will boot under various configurations (it will not; this system uses UEFI);
(3) manually editing the GRUB configuration file to refer to the correct UUID for the SSD in the new system;
(4) running boot-repair from the USB booted Ubuntu;
(5) running boot-repair from its own boot USB drive; and
(6) running boot-repair from its own boot USB drive in failsafe mode.

Boot repair running under Ubuntu purports to work but has no effect: looking at the logs, what seems to be happening is that it is performing the repair on the USB drive and not on the SSD, which error messages claim cannot be accessed because it is busy.

Boot repair from the bootable USB drive fails: on launching it (after the menu selection to choose a language and start the process), it shows scrolling text in the style of an old-fashioned Linux startup and then hangs with a black screen (and sometimes a flashing cursor in the top left). On restarting, the system will still not boot from the SSD. 

All of the important data on the SSD are backed up, so I could in principle just reformat the SSD and start again, but it would be very helpful if I could just allow it to boot and pick up where I left off without having to reconfigure everything from scratch again. 

If anyone could suggest anything that might remedy this, I should be most grateful.

---

### Post by ajgreeny on 2017-01-19
Run **Boot-Repair** again and follow the instructions there to run only the Boot-Info-Script.

**Do not run the default repair just yet** but simply copy back here the pastebin link you get which will show us a lot more about your system and may give us more info that can be used to help you.

---

### Post by jamespetts on 2017-01-19
Thank you for your reply. I am now at work, so am not able to re-format my USB drive, which currently has the bootable version of boot-repair, until I get home this evening. 

However, running it to-day, I find that it seems to boot into a Linux GUI, whereas, oddly, it did not yesterday. The only difference of which I can think is  that it is now connected via DisplayPort rather than HDMI.

I was able to run the boot-info-script, but the data that it produces is trapped on the NUC because the version of Linux that it is running will not recognise any of my network hardware and refuses to connect to the internet, either by ethernet or wifi (it connected fine by wifi when I used the Ubuntu 16.04 ISO on the USB drive). 

I could take pictures of the screen with the text file with my mobile telephone, but that might be a bit cumbersome. 

I can summarise one or two parts that seem to me to be significant if that would be of any help. Firstly, it states, under "suggested repair",

"The default repair of the Boot-Repair utility would not act on the MBR. Additional repair would be performed:  repair-filesystems"

It refers to my SSD as being on /dev/nvme0n1 (correctly identifying it as 256Gb), setting out its partition table as (in summary)

1: 537Mb, FAT32, EFI System Partition, boot flag
2: 512MB, ext2 (no name; presumably the swap file)
3: 255Gb (no filesystem or flags specified; presumably the main encrypted partition)

Under "PARTITIONS & DISKS" it lists:

nvme0n1p1: nvme0n1, not-setboot, no-grubenv no grub, no-docgrub, no -update-grub, 32, no-boot, no-os, is-correct-EFI, part-has-nofstab, part-has-no-fstab, no-nt, no-winload, no-recov-nor-hid, nobmgr, notwinboot, nopakmgr, nogrubinstall, no---usr, part-has-no-fstab, not-sep-usr, standard, not-far, /mnt/boot-sav/nvme0n1p1.

nvme0n1p2: nvme0n1, is-sepboot, grubenv-ok, nogrub, no-docgrub, -update-grub, 32, no-boot, no-os, not--efi--part, part-has-nofstab, part-has-no-fstab, no-nt, no-winload, no-recov-nor-hid, nobmgr, notwinboot, nopakmgr, nogrubinstall, no---usr, part-has-no-fstab, not-sep-usr, standard, not-far, /mnt/boot-sav/nvme0n1p2.

nvme0n1p3: nvme0n1, maybesepboot, no-grubenv, nogrub, no-docgrub, -update-grub, 32, no-boot, no-os, not--efi--part, part-has-nofstab, part-has-no-fstab, no-nt, no-winload, no-recov-nor-hid, nobmgr, notwinboot, nopakmgr, nogrubinstall, no---usr, part-has-no-fstab, not-sep-usr, standard, farbios, /mnt/boot-sav/nvme0n1p3.

Under "UEFI/Legacy Mode", it says,

"Unusual EFI: Please report this message to [email]boot.repair@gmail.com[/email]. BIOSis EFI-compatible and is setup in EFI-mode for this life-session. SecureBoot disabled maybe sec-boot, Please report this message to boot. [email]repair@gmail.com[/email]"

Under the lower part of blkid, it reports,

"efibootmgr -v
BootCurrent: 0002
Timeout: 1 seconds
BootOrder: 0001, 0002, 0000
Boot 0000* Windows Boot Manager Vendor (long string omitted)
Boot 0001* UEFI : Samsung SSD 950 Pro 256GB : Part 0: OS Bootloader ACPI (long string omitted)
Boot 0002* UEFI : SanDisk Extreme 0001 : Part 0 : OS Bootloader ACPI (long strong omitted)

Is any of this of assistance?

---

### Post by ajgreeny on 2017-01-19
> Is any of this of assistance? 
It might be to others but not me, I'm afraid, as I have no real knowledge of SSDs, though I believe there have been problems with NVMe disks.

Wait for others to come along who may be able to give you much better help than I can, or meantime, search to see if you can find more helpful info about NVMe disks.

---

### Post by leunam12 on 2017-01-19
Try the method on the link below, it works from the live USB, I have been able to repair GRUB that way when boot-repair fails.

[http://howtoubuntu.org/how-to-repair-restore-reinstall-grub-2-with-a-ubuntu-live-cd](http://howtoubuntu.org/how-to-repair-restore-reinstall-grub-2-with-a-ubuntu-live-cd)

---

### Post by oldfred on 2017-01-19
If you changed any UEFI/BIOS settings in UEFI, you must redo those. I found every time I update UEFI from vendor I have to redo them, so I make a list.

You have a newer NMVe drive. Not sure but think all references below to sda, need to use your nvme drive & partition.
/dev/nvme0n1p1 where nvme0n1 is drive and p1 is partition. Not sure then if you use p1 or 1 where in sda1 you just use 1??
And since default is first drive & first partition whether you can just not add anything & it installs correctly to your drive & partition or if you have to specify.

And you have the standard 3 physical partitions with UEFI & encryption which are the ESP - efi system partition, Ubuntu boot partition and encrypted partitions. Inside the LVM you probably have the / (root) & swap, but could have a separate /home or other partitions also. But you only see those with LVM tools.

You are not showing an Entry to boot Ubuntu.
Not sure if your NUC boots that or is like others that only boot "Windows Boot Manager" entry.
Since only booting Ubuntu you can change the standard Ubuntu entry to read "Windows Boot Manager".
I also like to add the fall back boot entry.

More details in link in my signature.

       You can heck entry is there, without having to run Boot-Repair.
sudo efibootmgr -v  

Efibootmgr defaults to first drive & first partition or sda1. You can just leave off the red part since your ESP is sda1.

 sudo efibootmgr -c -l "\EFI\UBUNTU\SHIMX64.EFI" -L ubuntu -d [COLOR=#ff0000]/dev/sdX -p Y[/COLOR]
where /dev/sdX is the disk and Y is the partition number.

If above entry does not directly boot from UEFI. You add a Windows entry that really still boots shimx64.efi.
**D:  **Use efibootmgr

 **d1**:  If Description has to be Windows then change UEFI description. Assumes ESP is sda1.
sudo efibootmgr -c -L "Windows Boot Manager" -l "\EFI\ubuntu\shimx64.efi" 

You may want to remove old Windows entry to avoid confusion.

       # from liveDVD or flash booted in UEFI mode and use efibootmgr
sudo efibootmgr -v
The "-v" option displays all the entries so you can confirm you're deleting the right one, and then you use the combination of "-b ####" (to specify the entry) and "-B" (to delete it). Examples #5 is delete:, with Ubuntu you need sudo, others must be at root. some need all 4 hex chars, others only need significant digits
sudo efibootmgr -b XXXX -B
man efibootmgr 
    
         
Optional:
The fallback or hard drive boot entry is /EFI/Boot/bootx64.efi. All external drives boot from that file name. Both Windows & Ubuntu use that to boot in UEFI mode(obviously different actual file).
Some systems have that folder & file in the ESP, some need it created. I copy shimx64.efi into that folder & rename shimx64.efi to bootx64.efi
Then add another hard drive or fallback entry into UEFI.
       sudo efibootmgr -c -g  -w -L "UEFI hard drive" -l '\EFI\Boot\bootx64.efi' -d /dev/sdX -p Y
sdX is drive, Y is efi partition

---

### Post by jamespetts on 2017-01-19
Thank you both for your suggestions. Leunam12 - I am afraid that the process on the web page to which you linked did not work, as the mount --bind commands failed.

Oldfred - I am afraid that I am having trouble following some of what you write. What do you mean, for example, when you write that I am not showing an entry to boot to Ubuntu? As to the BIOS settings, as the old computer was entirely non-functional, I cannot now be sure what those were. I have, however, tried various BIOS settings without success. Ought I perhaps to try secure boot? Would that do anything?

I also do not understand the instructions relating to the EFI Boot Manager. Running the command gives me,

"BootCurrent: 0002
Timeout: 1 seconds
BootOrder: 0001,0002,0000
Boot0000* Windows Boot Manager	VenHw(99e275e7-75a0-4b37-a2e6-c5385e6c00cb)WINDOWS.........x...B.C.D.O.B.J.E.C.T.=.{.9.d.e.a.8.6.2.c.-.5.c.d.d.-.4.e.7.0.-.a.c.c.1.-.f.3.2.b.3.4.4.d.4.7.9.5.}....................
Boot0001* UEFI : Samsung SSD 950 PRO 256GB : PART 0 : OS Bootloader	PciRoot(0x0)/Pci(0x1d,0x0)/Pci(0x0,0x0)/Unit(1)/HD(1,GPT,99a7d681-5134-4c1e-93dd-76d66073a68c,0x800,0x100000)..BO
Boot0002* UEFI : USB : SanDisk Extreme 0001 : PART 0 : OS Bootloader	PciRoot(0x0)/Pci(0x14,0x0)/USB(12,0)/HD(1,MBR,0x36,0x800,0x3ba26b0)..BO"

Also, when you write that my ESP is on /dev/sda1, what do you mean? I am not sure what an ESP is in this context. My /dev directory is as follows,

"autofs           hidraw2    loop4               port   ram8      tty12  tty30  tty49  ttyprintk  ttyS26   vcs2
block            hidraw3    loop5               ppp    ram9      tty13  tty31  tty5   ttyS0      ttyS27   vcs3
bsg              hpet       loop6               psaux  random    tty14  tty32  tty50  ttyS1      ttyS28   vcs4
btrfs-control    hugepages  loop7               ptmx   rfkill    tty15  tty33  tty51  ttyS10     ttyS29   vcs5
bus              hwrng      loop-control        ptp0   rtc       tty16  tty34  tty52  ttyS11     ttyS3    vcs6
char             i2c-0      mapper              pts    rtc0      tty17  tty35  tty53  ttyS12     ttyS30   vcs7
console          i2c-1      mcelog              ram0   sda       tty18  tty36  tty54  ttyS13     ttyS31   vcsa
core             i2c-2      mei0                ram1   sda1      tty19  tty37  tty55  ttyS14     ttyS4    vcsa1
cpu              i2c-3      mem                 ram10  sg0       tty2   tty38  tty56  ttyS15     ttyS5    vcsa2
cpu_dma_latency  initctl    memory_bandwidth    ram11  shm       tty20  tty39  tty57  ttyS16     ttyS6    vcsa3
cuse             input      mqueue              ram12  snapshot  tty21  tty4   tty58  ttyS17     ttyS7    vcsa4
disk             kmsg       net                 ram13  snd       tty22  tty40  tty59  ttyS18     ttyS8    vcsa5
dri              kvm        network_latency     ram14  stderr    tty23  tty41  tty6   ttyS19     ttyS9    vcsa6
ecryptfs         lightnvm   network_throughput  ram15  stdin     tty24  tty42  tty60  ttyS2      uhid     vcsa7
fb0              lirc0      null                ram2   stdout    tty25  tty43  tty61  ttyS20     uinput   vfio
fd               log        nvme0               ram3   tty       tty26  tty44  tty62  ttyS21     urandom  vga_arbiter
full             loop0      nvme0n1             ram4   tty0      tty27  tty45  tty63  ttyS22     usb      vhci
fuse             loop1      nvme0n1p1           ram5   tty1      tty28  tty46  tty7   ttyS23     userio   vhost-net
hidraw0          loop2      nvme0n1p2           ram6   tty10     tty29  tty47  tty8   ttyS24     vcs      zero
hidraw1          loop3      nvme0n1p3           ram7   tty11     tty3   tty48  tty9   ttyS25     vcs1"

Also, how would I remove the old Windows entry to avoid confusion?

Thank you again both for you help.

**Edit:**

The output of the sudo efibootmgr -c -L "Windows Boot Manager" -l "\EFI\ubuntu\shimx64.efi" command that you suggested was,

"** Warning ** : Boot0000 has same label Windows Boot Manager
GUID Partition Table Header signature is wrong: 0 != 5452415020494645
GUID Partition Table Header signature is wrong: 0 != 5452415020494645
GUID Partition Table Header signature is wrong: 0 != 5452415020494645
GUID Partition Table Header signature is wrong: 0 != 5452415020494645
GUID Partition Table Header signature is wrong: 0 != 5452415020494645
GUID Partition Table Header signature is wrong: 0 != 5452415020494645
BootCurrent: 0002
Timeout: 1 seconds
BootOrder: 0003,0001,0002,0000
Boot0000* Windows Boot Manager
Boot0001* UEFI : Samsung SSD 950 PRO 256GB : PART 0 : OS Bootloader
Boot0002* UEFI : USB : SanDisk Extreme 0001 : PART 0 : OS Bootloader
Boot0003* Windows Boot Manager"

---

### Post by oldfred on 2017-01-19
I do not know if error is just duplicate name or not. And then whether drive is sda1 or nmve.
Did you try adding the Ubuntu entry?
sudo efibootmgr -c -l "\EFI\UBUNTU\SHIMX64.EFI" -L ubuntu -d

And did you try the delete entry of 0000?
# from liveDVD or flash booted in UEFI mode and use efibootmgr
sudo efibootmgr -v
The "-v" option displays all the entries so you can confirm you're  deleting the right one, and then you use the combination of "-b ####"  (to specify the entry) and "-B" (to delete it). Examples #5 is delete:,  with Ubuntu you need sudo, others must be at root. some need all 4 hex  chars, others only need significant digits
sudo efibootmgr -b XXXX -B
man efibootmgr 

Then see if Windows using shim file entry works.

---

### Post by jamespetts on 2017-01-19
I have to say, I am now getting some very odd problems indeed: having shut down the NUC, on starting it again, it now refuses to boot from the USB drive unless legacy boot mode is enabled; however, if I boot into Linux from the USB drive with legacy boot mode enabled, it refuses to run efibootmgr. I do not understand why this behaviour has now changed or what to do about this.

---

### Post by oldfred on 2017-01-19
The BIOS/Legacy/CSM mode does not have the UEFI tools.
Did you turn on legacy boot in UEFI. Or some setting on USB ports and how they boot?

---

### Post by jamespetts on 2017-01-20
> **oldfred said:**
> The BIOS/Legacy/CSM mode does not have the UEFI tools.
Did you turn on legacy boot in UEFI. Or some setting on USB ports and how they boot?

When I do not turn legacy boot on, it refuses to boot with the USB drive.

When I do turn legacy boot on, it will boot into Ubuntu from the USB drive, but the UEFI tools will not work.

This behaviour is different from what it was earlier in the day yesterday, when I could boot from the USB drive with legacy boot disabled, and I do not understand why: the change in behaviour appears to have occurred without any intervention or discernible change in settings.

---

### Post by oldfred on 2017-01-20
What boot options do you have with legacy off.
Is UEFI Secure boot on?

---

### Post by jamespetts on 2017-01-20
No, secure boot is off. 

Apologies for the multiple postings above, incidentally: I was having trouble posting for some reason and the new posts were not showing up.

---

### Post by oldfred on 2017-01-20
Forum has ghosts, they sometimes interfere and other times are asleep & forum works fine.

Not sure what else to suggest.
Some have had issues and just created new flash drive.

Do you still have UEFI boot menu for internal drive, even if none of entries work?

---

### Post by jamespetts on 2017-01-20
Do you mean in the BIOS? The SSD does indeed show in the BIOS as having a bootloader: it just does not work when I try to use it.

**Edit:** Testing this again, the behaviour now of the USB drive when I have UEFI enabled is identical to that of the SSD: both the BIOS menu and the F10 boot menu recognise both devices as having bootloaders, yet attempting to boot from them fails with the "no bootable device detected" error message.

---

### Post by oldfred on 2017-01-20
That is typical of Secure boot on, or UEFI entries not being valid.
Perhaps your system only works with the "Windows Boot Manager" entry? Which most do not require, but some do. But those are mostly systems sold with Windows pre-installed.

---

### Post by jamespetts on 2017-01-20
Secure boot is definitely not on. What might cause the UEFI entries not to be valid; might it have happened that the USB drive's UEFI entry was corrupted by having run the commands above; would it be worthwhile re-flashing the USB drive? What might have caused the SSD's UEFI entry to be invalid, do you think?

---

### Post by oldfred on 2017-01-20
Not that familar with NUC, but it still should always boot flash drive, as long as you have UEFI set to allow UEFI boot.

It may be worth while to create new flash flash drive. Not sure how it could have gotten corrupted.

Have you tried a cold boot?
Sometimes that resets UEFI.
If fast boot is on in UEFI, it assumes you have no hardware nor configuration changes and default boots to old configuration.
Best to have fast boot off in UEFI.

My desktop allows on/off & and delay setting on UEFI boot, so when installing I have it off as a lot of settings & configurations change.
But once mostly configured I change to allow a 3 sec delay, but not full fast boot, as I may want to get into UEFI.
I also have a setting that allows standard boot from power off, so could also use that. But if that  was fast boot, I might not ever be able to get into a misconfigured system, without opening case & jumpering pins to reset.

---

### Post by jamespetts on 2017-01-20
Thank you for your reply. I do not have fast boot enabled in the BIOS. I have tried many attempts at cold boots, without any differences in behaviour from that described above. I will try again with a newly flashed USB drive and see whether I can boot into the USB drive using UEFI so that I can have another go at using the suggested tools.

---

### Post by jamespetts on 2017-01-20
I have just re-flashed the USB drive, and it now works in UEFI mode again - something must have corrupted the UEFI bootloader on the USB drive somehow. Very odd.

**Edit:** I have tried again to go through the steps set out in your original post (although I am not as clear as I might be about precisely what is required), but I am afraid that it does not help: on booting without the USB drive inserted, I still get a "no bootable drives detected" error message. Using the F10 boot menu, it claims to have a UEFI bootloader from the SSD, but selecting it has no effect: the screen flickers for a fraction of a second and then returns to the menu.

---

### Post by oldfred on 2017-01-20
Post this:
sudo efibootmgr -v

You may just have to have one entry that says "Windows Boot Manager".
But that can still be one that boots Ubuntu.

---

### Post by jamespetts on 2017-01-20
The output of that command is as follows (running from the USB drive):

BootCurrent: 0004
Timeout: 1 seconds
BootOrder: 0002,0004,0000,0003,0001
Boot0000* Windows Boot Manager	VenHw(99e275e7-75a0-4b37-a2e6-c5385e6c00cb)WINDOWS.........x...B.C.D.O.B.J.E.C.T.=.{.9.d.e.a.8.6.2.c.-.5.c.d.d.-.4.e.7.0.-.a.c.c.1.-.f.3.2.b.3.4.4.d.4.7.9.5.}....................
Boot0001* ubuntu	VenHw(99e275e7-75a0-4b37-a2e6-c5385e6c00cb)
Boot0002* UEFI hard drive	HD(1,GPT,99a7d681-5134-4c1e-93dd-76d66073a68c,0x800,0x100000)/File(\EFI\Boot\bootx64.efi)
Boot0003* Windows Boot Manager	VenHw(99e275e7-75a0-4b37-a2e6-c5385e6c00cb)
Boot0004* UEFI : USB : SanDisk Extreme 0001 : PART 0 : OS Bootloader	PciRoot(0x0)/Pci(0x14,0x0)/USB(13,0)/HD(1,MBR,0x4294967194,0x800,0x3ba26b0)..BO

---

### Post by oldfred on 2017-01-21
The long number is the GUID of the ESP partition for UEFI boot, not sure what it shows for CSM/BIOS boot.

But you have two different GUIDs. GUID is different than UUID.

Post this where partUUID is GUID:
       lsblk -o +PARTUUID /dev/sda 
Or in your case it may be

 lsblk -o +PARTUUID /dev/nvme0n1

---

### Post by jamespetts on 2017-01-21
The output of that command is:

NAME        MAJ:MIN RM   SIZE RO TYPE MOUNTPOINT PARTUUID
nvme0n1     259:0    0 238.5G  0 disk            
&#9500;&#9472;nvme0n1p1 259:1    0   512M  0 part            99a7d681-5134-4c1e-93dd-76d66073a68c
&#9500;&#9472;nvme0n1p2 259:2    0   488M  0 part            de2ccd13-dad7-4cd7-9a1a-19dbcf3da639
&#9492;&#9472;nvme0n1p3 259:3    0 237.5G  0 part            5b0e98ed-0e93-4f6e-beb5-b3b8b82ca557

---

### Post by oldfred on 2017-01-21
Your only entry in the ESP for nvme0n1p1 is 0002 as both are 99a... 
All the others are 99e....

That was the new fallback or hard drive entry. Does that work?

---

### Post by jamespetts on 2017-01-21
I am afraid that I do not understand the question; does what work? Incidentally, the 0002 entry is the one created manually following your instructions earlier in this thread.

---

### Post by oldfred on 2017-01-21
And that new fallback entry is the only one that looks like it might work.
All the others are referring to a different boot partition.

---

### Post by jamespetts on 2017-01-21
I do not know what to do about that. However, the new entry does not work: the system will still not boot from the SSD.

---

### Post by oldfred on 2017-01-21
Rerun Boot-Repair in UEFI mode and do a full uninstall/reinstall of grub using the advanced options.
       [https://sourceforge.net/p/boot-repair/home/Home/](https://sourceforge.net/p/boot-repair/home/Home/) 
    
After that rerun the Summary Report and post link to it.

---

### Post by jamespetts on 2017-01-21
I cannot make boot-repair run in UEFI mode, as the "GRUB locations" is greyed out. However, the pastebin is here:

[http://paste2.org/pnB1GvvG](http://paste2.org/pnB1GvvG)

---

### Post by oldfred on 2017-01-21
It says you booted in UEFI boot mode in Summary Report.
In advanced mode you should be able to run the full uninstall/reinstall of grub2.

Once you start to boot, you can tell which mode you are in my the screen.
 Shows install with screen shots. Both BIOS purple accessibility screen & UEFI black grub menu screen
 [https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI) 

Delete both Windows entries with efibootmgr & add a new one. details in post #6
Delete 0000 & 0003

And add the new Windows entry that boots shim. As in post #6
**d1**:  If Description has to be Windows then change UEFI description. Assumes ESP is sda1. Should work with your nvme drives if the other entry worked.
sudo efibootmgr -c -L "Windows Boot Manager" -l "\EFI\ubuntu\shimx64.efi"

---

### Post by jamespetts on 2017-01-21
I am afraid that the GRUB location, GRUB options and MBR options are all greyed out in Boot Repair. Am I missing something? 

I have deleted entries 0000 and 0003, although I am afraid that I also accidentally deleted entry 0001. 

Running the command "sudo efibootmgr -c -g -w -L "UEFI hard drive" -l '\EFI\Boot\bootx64.efi' -d /dev/nvme0 -p 1" gives the error:

```

** Warning ** : Boot0002 has same label UEFI hard drive
Cannot stat non-block or non-regular file
efibootmgr: Could not set variable: No such file or directory
efibootmgr: Could not prepare boot variable: No such file or directory

```

Running the command sudo efibootmgr -c -L "Windows Boot Manager" -l "\EFI\ubuntu\shimx64.efi" gives the following output:

```

** Warning ** : Boot0000 has same label Windows Boot Manager
GUID Partition Table Header signature is wrong: 0 != 5452415020494645
GUID Partition Table Header signature is wrong: 0 != 5452415020494645
GUID Partition Table Header signature is wrong: 0 != 5452415020494645
GUID Partition Table Header signature is wrong: 0 != 5452415020494645
GUID Partition Table Header signature is wrong: 0 != 5452415020494645
GUID Partition Table Header signature is wrong: 0 != 5452415020494645
BootCurrent: 0004
Timeout: 1 seconds
BootOrder: 0001,0000,0002,0004
Boot0000* Windows Boot Manager
Boot0002* UEFI hard drive
Boot0004* UEFI : USB : SanDisk Extreme 0001 : PART 0 : OS Bootloader
Boot0001* Windows Boot Manager

```

It does not look right that there are two Windows Boot Managers. Are any further steps required at this stage?

---

### Post by oldfred on 2017-01-22
Does not look like you deleted the correct entries.
Always run this first:

sudo efibootmgr -v

And then it looks like efibootmgr only uses default of sda.
So the entry you used with drive & partition like -d /dev/nvme0 -p 1 seems to work.
But the one without the specific entry does not.

Houseclean correct entries and add new entries again but using -d /dev/nvme0 -p 1

Did you run Boot-Repair's full uninstall/reinstall of grub?

---

### Post by jamespetts on 2017-01-22
I still find the instructions somewhat hard to follow in a number of places. Perhaps it would be best if I were to copy and paste the complete set of instructions together with their outputs since my last post based on what you have suggested so that you can see whether I have got this right or not, and, if not, where I erred. 

Is this correct so far?

```

ubuntu@ubuntu:~$ sudo efibootmgr -v
BootCurrent: 0004
Timeout: 1 seconds
BootOrder: 0001,0000,0002,0004
Boot0000* Windows Boot Manager	HD(1,MBR,0x4294967194,0x800,0x3ba26b0)/File(\EFI\ubuntu\shimx64.efi)
Boot0001* Windows Boot Manager	HD(1,MBR,0x4294967194,0x800,0x3ba26b0)/File(\EFI\ubuntu\shimx64.efi)
Boot0002* UEFI hard drive	HD(1,GPT,99a7d681-5134-4c1e-93dd-76d66073a68c,0x800,0x100000)/File(\EFI\Boot\bootx64.efi)
Boot0004* UEFI : USB : SanDisk Extreme 0001 : PART 0 : OS Bootloader	PciRoot(0x0)/Pci(0x14,0x0)/USB(13,0)/HD(1,MBR,0x4294967194,0x800,0x3ba26b0)..BO
ubuntu@ubuntu:~$ lsblk -o +PARTUUID /dev/nvme0n1 
NAME        MAJ:MIN RM   SIZE RO TYPE MOUNTPOINT              PARTUUID
nvme0n1     259:0    0 238.5G  0 disk                         
&#9500;&#9472;nvme0n1p1 259:4    0   512M  0 part /mnt/boot-sav/nvme0n1p1 99a7d681-5134-4c1e-93dd-76d66073a68c
&#9500;&#9472;nvme0n1p2 259:5    0   488M  0 part /mnt/boot-sav/nvme0n1p2 de2ccd13-dad7-4cd7-9a1a-19dbcf3da639
&#9492;&#9472;nvme0n1p3 259:6    0 237.5G  0 part                         5b0e98ed-0e93-4f6e-beb5-b3b8b82ca557
ubuntu@ubuntu:~$ sudo efibootmgr -b 0000 -B
BootCurrent: 0004
Timeout: 1 seconds
BootOrder: 0001,0002,0004
Boot0001* Windows Boot Manager
Boot0002* UEFI hard drive
Boot0004* UEFI : USB : SanDisk Extreme 0001 : PART 0 : OS Bootloader
ubuntu@ubuntu:~$ sudo efibootmgr -b 0001 -B
BootCurrent: 0004
Timeout: 1 seconds
BootOrder: 0002,0004
Boot0002* UEFI hard drive
Boot0004* UEFI : USB : SanDisk Extreme 0001 : PART 0 : OS Bootloader
ubuntu@ubuntu:~$ sudo efibootmgr -c -g -w -L "UEFI hard drive" -l '\EFI\Boot\bootx64.efi' -d /dev/nvme0 -p 1
** Warning ** : Boot0002 has same label UEFI hard drive
Cannot stat non-block or non-regular file
efibootmgr: Could not set variable: No such file or directory
efibootmgr: Could not prepare boot variable: No such file or directory
ubuntu@ubuntu:~$ sudo efibootmgr -c -l "\EFI\UBUNTU\SHIMX64.EFI" -L ubuntu -d /dev/nvme0 -p 1
Cannot stat non-block or non-regular file
efibootmgr: Could not set variable: No such file or directory
efibootmgr: Could not prepare boot variable: No such file or directory
ubuntu@ubuntu:~$ sudo efibootmgr -c -l "\EFI\UBUNTU\SHIMX64.EFI" -L ubuntu -d /dev/nvme0n1 -p 1
BootCurrent: 0004
Timeout: 1 seconds
BootOrder: 0000,0002,0004
Boot0002* UEFI hard drive
Boot0004* UEFI : USB : SanDisk Extreme 0001 : PART 0 : OS Bootloader
Boot0000* ubuntu
ubuntu@ubuntu:~$ sudo efibootmgr -c -g -w -L "UEFI hard drive" -l '\EFI\Boot\bootx64.efi' -d /dev/nvme0n1 -p 1
** Warning ** : Boot0002 has same label UEFI hard drive
BootCurrent: 0004
Timeout: 1 seconds
BootOrder: 0001,0000,0002,0004
Boot0000* ubuntu
Boot0002* UEFI hard drive
Boot0004* UEFI : USB : SanDisk Extreme 0001 : PART 0 : OS Bootloader
Boot0001* UEFI hard drive
ubuntu@ubuntu:~$ 

```

---

### Post by oldfred on 2017-01-22
I now see this difference.
> Boot0001* Windows Boot Manager	HD(1,[COLOR=#ff0000]MBR[/COLOR],0x4294967194,0x800,0x3ba26b0)/File(\EFI\ubuntu\shimx64.efi)
Boot0002* UEFI hard drive	HD(1,[COLOR=#ff0000]GPT[/COLOR],99a7d681-5134-4c1e-93dd-76d66073a68c,0x800,0x100000)/File(\EFI\Boot\bootx64.efi)


I do not know where MBR comes from, but suspect it is because we ran commands without the specific nvme device and it used default of sda.
And your sda device must be MBR or flash drive is used as default then.

So make sure you delete all the entries with MBR or both Windows entries.
And then add a new Windows entry but include the nvme device & partition in entry.
And immediately check that is is correct or using gpt & the 99a..... partiiton like Boot0002.

Did you run Boot-Repair's Advanced mode and 'use the standard efi file'
That copies shimx64.efi to /EFI/Boot/bootx64.efi so then your Boot0002 should work. Or we can manually copy shim.

---

### Post by jamespetts on 2017-01-22
One thing on which I am not clear before proceeding further: when you refer to running Boot Repair in advanced mode, do you mean selecting "advanced options", or is there a command line switch or something? When I select advanced options, GRUB location, GRUB options and MBR options are all greyed out, and there is no "use the standard efi file" option anywhere.

---

### Post by oldfred on 2017-01-22
This shows Boot-Repair's screens. And examples look like the older Boot-Repair.
 [https://sourceforge.net/p/boot-repair/home/Home/](https://sourceforge.net/p/boot-repair/home/Home/) 

Are you running the old Boot-Repair ISO, which now is not current.
Or adding Boot-Repair into the Ubuntu installer?

Yann says it is on by default in newer version.
[https://bugs.launchpad.net/ubuntu/+bug/1531178](https://bugs.launchpad.net/ubuntu/+bug/1531178)

---

### Post by jamespetts on 2017-01-23
I added Boot Repair to the Ubuntu installer. I do not get the same options as are shown in that screenshot, however. Under "Main options", I get only "Backup partition tables, bootselectors and logs", and a tick box for "Repair file systems" and "Repair Wubi filesystems", the latter of which is greyed out.

---

### Post by oldfred on 2017-01-23
My copy of Boot-Repair on main screen shows it but it is not checked by default.
What version are you running?

---

### Post by jamespetts on 2017-01-23
Mine does not look like that at all: it lacks all but the "Repair file systems" and "Repair Wubi filesystems" tickboxes and the "Backup tables..." (etc.) box at the top I installed it using the instructions [here](https://help.ubuntu.com/community/Boot-Repair).

---

### Post by oldfred on 2017-01-23
Are you using the Second option to install into the Ubuntu live installer.
That way you get the newest version.
The ISO seems be be a couple of years old, so is not now current versions.

---

### Post by jamespetts on 2017-01-23
I am not using the ISO - I am using these commands:

```

sudo add-apt-repository ppa:yannubuntu/boot-repair
sudo apt-get update
sudo apt-get install -y boot-repair && boot-repair

```

---

### Post by oldfred on 2017-01-23
Then it may not show if you boot in BIOS mode as it cannot make that change.
And only shows if you boot in UEFI boot mode.

So your one report said you had booted in UEFI boot mode, but before you said you had troubles booting in UEFI.
Can you consistently boot in UEFI boot mode from a UEFI boot entry UEFI:flash drive where flash drive is name/label/brand of flash drive.

---

### Post by jamespetts on 2017-01-23
I am now booting in UEFI mode so far as I can tell - the problems that I had booting in UEFI mode were caused, I think, by having corrupted the boot partition on the USB drive and were fixed when I re-flashed it.

---

### Post by oldfred on 2017-01-23
I lost track of where we are.

Did you houseclean obsolete Windows entries in UEFI.
Did you update UEFI with new "Windows" entry that really boots shim using your NVMe drive not default?
Did you run Boot-Repair when booted in UEFI mode?

In link in my signature are commands for manually copying /EFI/ubuntu/shimx64.efi to /EFI/Boot/bootx64.efi, if Boot-Repair has not copied it. You have to review files sizes to know if copied as many systems have bootx64.efi but it may be a copy of the Windows .efi boot file.

---

### Post by jamespetts on 2017-01-23
I have not always been able to follow everything that you write, but I have tried as best as I can to execute the suggestions that you have provided. I did delete the old entries as you suggested; I attempted to add a new "Windows" entry, but I am unsure whether that succeeded, and, if it did not succeed, what I could do to make it succeed. I did boot in UEFI mode to the USB drive. 

As to the last paragraph - do I have to do that *before* running boot-repair?

---

### Post by oldfred on 2017-01-24
If Boot-Repair has not copied /EFI/ubuntu/shimx64.efi to /EFI/Boot/bootx64.efi then you need to manually do it.
Check file sizes to know.

After running a command always check to see if new entry is there & refers to your correct GUID partition.
sudo efibootmgr -v

---

### Post by jamespetts on 2017-01-24
I am having real difficulty in understanding what the nature of the underlying problem is and how any of these tools interact with it. There are a great many related issues the relationship between which I do not understand, so I can do no more than follow the precise instructions that you have given (I am not able to follow the more general instructions without a much more detailed understanding of how all of these systems work, and I cannot find a way of learning about this within a time that is less than the time that it would take simply to reformat my SSD and re-install Ubuntu afresh, including the time taken to set it up again). It is therefore very unclear to me whether I have completely followed all of your suggestions correctly or not: I have tried to report with precision what I have done and what the output of what I have done has been wherever possible.

Given the amount of time that has elapsed since the original problem was reported seemingly without any progress, do you think that there is a real prospect of me saving any time by continuing to pursue these suggested solutions rather than simply reformatting my SSD and starting again? The purpose of this course of action was to save time, and the amount of time being now consumed seems to be increasingly inconsistent with that aim.

For reference, I reproduce the output of what I believe that the latest suggested commands are (together with the commands themselves) below. 

```

ubuntu@ubuntu:~$ sudo efibootmgr -v 
BootCurrent: 0003
Timeout: 1 seconds
BootOrder: 0001,0003,0000,0002
Boot0000* ubuntu	VenHw(99e275e7-75a0-4b37-a2e6-c5385e6c00cb)
Boot0001* UEFI hard drive	HD(1,GPT,99a7d681-5134-4c1e-93dd-76d66073a68c,0x800,0x100000)/File(\EFI\Boot\bootx64.efi)
Boot0002* UEFI hard drive	VenHw(99e275e7-75a0-4b37-a2e6-c5385e6c00cb)
Boot0003* UEFI : USB : SanDisk Extreme 0001 : PART 0 : OS Bootloader	PciRoot(0x0)/Pci(0x14,0x0)/USB(13,0)/HD(1,MBR,0x4294967194,0x800,0x3ba26b0)..BO
ubuntu@ubuntu:~$ sudo cp  /EFI/ubuntu/shimx64.efi /EFI/Boot/bootx64.efi /EFI/Boot/bootx64.efi
cp: target '/EFI/Boot/bootx64.efi' is not a directory
ubuntu@ubuntu:~$ sudo cp  /EFI/ubuntu/shimx64.efi /EFI/Boot/bootx64.efi
cp: cannot stat '/EFI/ubuntu/shimx64.efi': No such file or directory

```

Does any of this assist?

---

### Post by oldfred on 2017-01-24
Since you are in the live install, but want to move files in the actual install, you cannot just say to copy a file from its location in the working install as you can usually do when booted into the system. So mount your ESP/efi partition, you may have to create /EFI/Boot folder, but should have the /EFI/ubuntu folder.

       From live installer booted in UEFI mode, mount the efi partition on hard drive, lines with # are comments only: Mount ESP - efi system partition. check which partition is FAT32 with boot flag. Often sda1 or sda2 but varies.
# if your ESP is not sda1 change this to correct partition
sudo mount /dev/sda1 /mnt
only if /EFI/Boot not already existing, run the mkdir command,
sudo mkdir /mnt/EFI/Boot
sudo cp /mnt/EFI/ubuntu/* /mnt/EFI/Boot
# If new folder created, the bootx64.efi will not exist, skip backup command
sudo mv /mnt/EFI/Boot/bootx64.efi /mnt/EFI/Boot/bootx64.efi.backup
# make grub be hard drive boot entry in UEFI. Then boot hard drive entry in UEFI menu.
sudo mv /mnt/EFI/Boot/grubx64.efi /mnt/EFI/Boot/bootx64.efi 

Then see if you can boot 0001, but may need to delete 0002 as it has same name, but is not the UEFI boot.

---

### Post by jamespetts on 2017-01-26
Thank you for that.

Having run those commands, when I now try to boot from the internal SSD, I simply get a GRUB shell. When I enter the command, "boot", it gives me an error message stating that I need to load a kernel first. The boot-repair app (loading it from the USB drive live install again) behaves as I described earlier, i.e with the greyed out options. I have not tried the "recommended repair" as last time that I tried this, it stopped my USB drive from booting in UEFI mode. 

There has been at least a little progress. Are you in a position to assist as to how I might be able to boot into the system itself?

Thank you again for your help so far.

---

### Post by oldfred on 2017-01-26
Which way are you booting UEFI or BIOS. This shows actual first boot screen, so you know:
 Shows install with screen shots. Both BIOS purple accessibility screen & UEFI black grub menu screen
 [https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI) 


Getting grub> or grub rescue says the grub is misconfigured or not fully installed. Or you fixed one mode, but are booting in the other mode that has left over older grub version.
Usually running Boot-Repair's advanced option to fully uninstall/reinstall grub & latest kernel updates system to correctly boot.
But that must be the in the correct UEFI or BIOS boot mode, that you want & then when booting from UEFI/BIOS the same boot mode as you reinstalled grub.

You just need to always boot UEFI or always boot BIOS.
And then make sure UEFI is set to use that mode both for installed system and flash drive.

---

### Post by jamespetts on 2017-01-26
I do not get the normal GRUB menu - I get a GRUB command line shell (not pictured on that web page). It is black with white text and has a grub> prompt. 

I am booting in UEFI mode (and legacy boot is disabled in the BIOS, as it was when I ran the commands that you suggested): the menu that I get when I press F10 gives only one possible entry (when the USB drive is removed). 

As to boot-repair's advanced options, as indicated before, the GRUB options are always greyed out and the options that you recommend that I select are simply not there. I am definitely running in UEFI boot mode when this occurs. 

The output of sudo efibootmgr - v is:

```

ubuntu@ubuntu:~$ sudo efibootmgr -v
BootCurrent: 0003
Timeout: 1 seconds
BootOrder: 0001,0003,0000,0002
Boot0000* ubuntu	VenHw(99e275e7-75a0-4b37-a2e6-c5385e6c00cb)
Boot0001* UEFI hard drive	HD(1,GPT,99a7d681-5134-4c1e-93dd-76d66073a68c,0x800,0x100000)/File(\EFI\Boot\bootx64.efi)
Boot0002* UEFI hard drive	VenHw(99e275e7-75a0-4b37-a2e6-c5385e6c00cb)
Boot0003* UEFI : USB : SanDisk Extreme 0001 : PART 0 : OS Bootloader	PciRoot(0x0)/Pci(0x14,0x0)/USB(12,0)/HD(1,MBR,0x4294967194,0x800,0x3ba26b0)..BO

```

---

### Post by oldfred on 2017-01-26
I think the Boot0000 entry will not work. It that the one giving you errors?

But the entry Boot0001 should work if shim copied  to bootx64.efi, but Boot0002 will not work either.

You should use efibootmgr to delete Boot0000 and Boot0002, if for not other reason than to avoid confusion on which entry you are booting.
Normal menu entry only shows name/label, so those with same name may be incorrectly selected.

---

### Post by jamespetts on 2017-01-26
Thank you for that. I tried deleting entries 0000 and 0002, but rebooting gave me the same grub> prompt.

---

### Post by oldfred on 2017-01-26
I think I suggested before to add a Windows entry.
Do you have /EFI/ubuntu & /EFI/Boot folders in ESP?


efibootmgr defaults to sda and first partition, Did we find you had to use your nvme drive in entry.
Is that how you got correct entry you have for hard drive? Then include it as shown
is correct entry nvme0n1 or nvme0? 

sudo efibootmgr -v
           sudo efibootmgr -c -L "Windows Boot Manager" -l "\EFI\ubuntu\shimx64.efi" -d /dev/nvme0n1 -p 1
# then confirm new entry is there:
sudo efibootmgr -v

# and see if you can boot Windows entry

---

### Post by jamespetts on 2017-01-26
Thank you for that. The output from the suggested commands is as follows:

```

ubuntu@ubuntu:~$ sudo efibootmgr -v
BootCurrent: 0002
Timeout: 1 seconds
BootOrder: 0001,0002
Boot0001* UEFI hard drive	HD(1,GPT,99a7d681-5134-4c1e-93dd-76d66073a68c,0x800,0x100000)/File(\EFI\Boot\bootx64.efi)
Boot0002* UEFI : USB : SanDisk Extreme 0001 : PART 0 : OS Bootloader	PciRoot(0x0)/Pci(0x14,0x0)/USB(12,0)/HD(1,MBR,0x4294967194,0x800,0x3ba26b0)..BO
ubuntu@ubuntu:~$ sudo efibootmgr -c -L "Windows Boot Manager" -l "\EFI\ubuntu\shimx64.efi" -d /dev/nvme0n1 -p 1
BootCurrent: 0002
Timeout: 1 seconds
BootOrder: 0000,0001,0002
Boot0001* UEFI hard drive
Boot0002* UEFI : USB : SanDisk Extreme 0001 : PART 0 : OS Bootloader
Boot0000* Windows Boot Manager
ubuntu@ubuntu:~$ sudo efibootmgr -v
BootCurrent: 0002
Timeout: 1 seconds
BootOrder: 0000,0001,0002
Boot0000* Windows Boot Manager	HD(1,GPT,99a7d681-5134-4c1e-93dd-76d66073a68c,0x800,0x100000)/File(\EFI\ubuntu\shimx64.efi)
Boot0001* UEFI hard drive	HD(1,GPT,99a7d681-5134-4c1e-93dd-76d66073a68c,0x800,0x100000)/File(\EFI\Boot\bootx64.efi)
Boot0002* UEFI : USB : SanDisk Extreme 0001 : PART 0 : OS Bootloader	PciRoot(0x0)/Pci(0x14,0x0)/USB(12,0)/HD(1,MBR,0x4294967194,0x800,0x3ba26b0)..BO
ubuntu@ubuntu:~$ 

```

I am about to reboot and try to see whether this works, and will edit this message to update with the result.

**Edit**: Having just checked, I am afraid that this does not assist: I still get the grub> prompt. The only entry in the boot menu (accessed by pressing F10 when booting) is a single entry marked as a UEFI Windows boot loader.

---

### Post by oldfred on 2017-01-26
Your f10 only shows the Windows entry?
What entry then did you boot before? It should show the UEFI Hard Drive entry also.
Both those now look correct, unless something else has changed.

It may still be settings in UEFI, but I am not familiar with your UEFI.

You need Secure Boot off. But you also can try with it on as shimx64.efi is the secure boot version. But only is kernel installed is signed version.

Most need UEFI on and BIOS/CSM off, but a few systems need CSM on, but still select UEFI boot only. 
Not exactly sure how that works, as my system is either UEFI or CSM. 
And I have to select UEFI only, as even a choice of UEFI or BIOS only booted in BIOS mode.

---

### Post by jamespetts on 2017-01-26
Legacy boot is disabled in the BIOS. Both the SSD and the USB drive boot via UEFI.

---

### Post by jamespetts on 2017-01-26
I am a little confused: I think that the order of posts has become corrupted somehow and possibly posts deleted, since I do not think that my last post is actually a reply to your last post.

To reply to your last post, yes, the Windows UEFI entry is the only entry in the F10 menu. I should note that I have never had Windows installed on this computer. Secure boot is definitely off. I can try with secure boot on if you think that that will help.

**Edit**: Booting with secure boot enabled did not help: I still get the grub> prompt.

---

### Post by oldfred on 2017-01-26
I know you did not have Windows, but some computers only boot Windows entry, so if not dual booting we make a Windows entry, but have that entry actually boot shimx64.efi or grub/Ubuntu.

If not UEFI settings, somewhere and your UEFI entries look ok, not sure what else to suggest.

I would like the full reinstall of grub from Boot-Repair. 
Do not know why it would have greyed out settings if booting in UEFI mode.

We can do a full chroot into install to reinstall grub. 
chroot is CHange ROOT to boot with kernel on flash drive, but then change to use it for installed system to run updates from inside your installed system.

If Boot-Repair does not work when booted in UEFI mode, then I can post commands for chroot.

---

### Post by jamespetts on 2017-01-27
I should be grateful if you could - I am not sure how otherwise to deal with this.

---

### Post by oldfred on 2017-01-27
Lets first check one or two things.

At the grub? when booting does pressing enter do anything?
And also try this, if enter does not do anything:
ls
       ls (hd0,1) 

    
There is a small 3 line grub.cfg in /EFI/ubuntu and that must have the correct partition & UUID.

Post results of these:
Standard drive mount
sudo mount /dev/sda1 /mnt
or your nvme device?
sudo mount /dev/nvme0n1p1      /mnt (is this what works as I still not sure about nvme devices)

cd /mnt/EFI/ubuntu
ls -l
cat grub.cfg
blkid
# confirm that UUID in grub.cfg matches UUID of first partition.

If any command does not work add sudo at beginning, but live installer should not need it.

       UEFI chroot (you may need to use nvme0n1 in all places it mentions sda and nvme0n1p1 where it mentions sda1 or sda#.
[http://askubuntu.com/questions/53578/can-i-install-in-uefi-mode-with-the-alternate-installer/57380#57380](http://askubuntu.com/questions/53578/can-i-install-in-uefi-mode-with-the-alternate-installer/57380#57380)

---

### Post by jamespetts on 2017-01-27
To answer your questions: yes, the grub> prompt is responsive. Pressing enter yields another grub> prompt on the next line. 

The result of the ls command is:

(hd0) (hd0,gpt3) (hd0,gpt2) (hd0,gpt1)

The result of the ls (hd0,1) command is

(ha0,1): Filesystem is fat

Do you mean me to attempt the other commands at the grub> prompt or having loaded Ubuntu from the USB drive?

---

### Post by oldfred on 2017-01-27
I would like to see the contents of the /EFI/ubuntu/grub.cfg
Just to see if it has correct partition & UUID. That could be the type of error that gives you just the grub> prompt as it cannot find correct / (root) partition with the rest of grub & kernels. 
It may not have been updated from before as you did have some inconsistency on GUIDs in UEFI which would say some partitions changed. 

A full reinstall of grub would also fix any errors, but you need either chroot or Boot-Repair to do that. But lets check /EFI/ubuntu/grub.cfg first.

---

### Post by LostFarmer on 2017-01-27
oldfred-- (efi boot only , not tested for MBR) In case you have not found out yet, grub has made a change with version (2.02~beta2-36ubuntu3.7) , it no longer uses /EFI/ubuntu/grub.cfg.  The gpt# and path is embeded into grubx64.efi file.  With the new grub it is also possible to boot directly the kernel without the use of the grub.cfg.  

I copied initrd.img and vmlinuz to /EFI/ubuntu/ and using efibootmgr wrote the needed info to the firmware.  The command I used was:
 sudo efibootmgr -c -g -L "Ubuntu (stub)" -l '\EFI\ubuntu\vmlinuz' -u "root=UUID=f0cbd27a-838c-4db5-aa31-ce6cab378594 ro quiet rootfstype=ext4 add_efi_memmap initrd=\\EFI\\ubuntu\\initrd.img"

The basic command was from  [https://wiki.debian.org/EFIStub](https://wiki.debian.org/EFIStub).  Note: the above does NOT permit duel booting selection from grub.

The above is from a new install of ubuntu-16.04 and updating grub with synaptic .  (testing for a grub problem on a usb-mbr, will not see internal hdd).

Do not know what grub version would be installed with ( boot-repair ).

---

### Post by jamespetts on 2017-01-27
Thank you for your reply. The contents of grub.cfg are:

```

cat grub.cfg
search.fs_uuid bcd3d811-c567-4438-a382-8a0f1c2b8ca2 root 
set prefix=($root)'/grub'

```

I am afraid that I am also mystified as to why boot-repair does not work properly every time that I install it from the USB drive boot. 

LostFarmer - do I need to use the command that you set out in order to try to make Grub work again, or do I need to modify the UUID (and, if so, to what)? I should note that I am not interested in dual booting using GRUB - I only want to use Ubunu on this machine.

---

### Post by oldfred on 2017-01-27
Thanks LostFarmer. I need to experiment with that.
I have changed the GRUB_DISTRIBUTOR in /etc/default/grub and had UEFI install another copy in the ESP with that name. But it always boots based on the grub.cfg in /EFI/ubuntu.

For reference Boot-Repair normally has you chroot into install and installs the version of grub that is current with that install.

@jamespetts
Your grub.cfg does not look correct. Not sure if update to newer grub has applied to your install.

My grub.cfg for reference.
```
cat /boot/efi/EFI/ubuntu/grub.cfg 
search.fs_uuid 5c1e1a3f-261f-4da5-a0c2-8f479b3039de root hd0,gpt2 
set prefix=($root)'/boot/grub'
configfile $prefix/grub.cfg

```

If LostFarmer's updates have not applied your grub.cfg is incomplete.
You posted before that your UUID of your install was from Boot-Repair Summary report in post #30.
/dev/nvme0n1p2    41b8a819-3f07-4a7e-a13a-af3c667f7b3a

I assume while they have said they updated grub to work with NVMe drives, it is not correctly adding them.

Change your grub.cfg to this (assuming it still is (hd0, gpt2):
```
search.fs_uuid 41b8a819-3f07-4a7e-a13a-af3c667f7b3a root hd0,gpt2 
set prefix=($root)'/boot/grub'
configfile $prefix/grub.cfg

```

---

### Post by jamespetts on 2017-01-27
Thank you for that. I updated my grub.cfg as recommended, but attempting to boot from the SSD again resulted in the grub> prompt.

---

### Post by oldfred on 2017-01-27
Was that with flash drive unplugged?

Then all I can suggest is the full chroot.
But the combination of UEFI, LVM, encrypted partitions makes it difficult to chroot into your install.

When in Boot-Repair are you un-encrypting your encrypted LVM? It needs that to work correctly.
Perhaps that is why many options are not shown.

I really do not know LVM nor encryption. I consider that an advanced install. 
But some need full drive encryption and that uses LVM.

You will need some combination of these posts and the one's on chroot I posted above.
And where sda or sdaX is shown, you probably need to use your NVMe drive & partition.

 Includes chroot:
[https://help.ubuntu.com/community/EncryptedPrivateDirectory/#Live_CD_method_of_opening_a_encrypted_home_directory](https://help.ubuntu.com/community/EncryptedPrivateDirectory/#Live_CD_method_of_opening_a_encrypted_home_directory)
[http://askubuntu.com/questions/719409/how-to-reinstall-grub-from-a-liveusb-if-the-partition-is-encrypted-and-there-i?rq=1](http://askubuntu.com/questions/719409/how-to-reinstall-grub-from-a-liveusb-if-the-partition-is-encrypted-and-there-i?rq=1) 

If you really do not need full drive encryption, a re-install may be easier.

---

### Post by jamespetts on 2017-01-27
Yes, that was with the USB drive unplugged.

As to Boot Repair, I do not remember there being any option to unencrypt the logical volume manager. Where would that option be located and how would I find it? I wanted full drive encryption because I keep confidential information on the device related to my professional legal practice and it is carried from place to place, so there is a possibility of it being lost or stolen. 

May I ask which combination of the posts that I will need? I am not really sure how to interpret that last statement to produce a set of steps that I can use to make my device work again.

---

### Post by oldfred on 2017-01-27
I believe the bottom line is that grub only installs to drive seen as sda.
And in your system, it is installing to sda which is your flash drive, not to your internal drive which is the NVMe device.
Would you log into launchpad and add your issue to this bug. Explain you are installing to an internal NVMe drive, and flash drive is sda, so grub never correctly installs.
[https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/1173457](https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/1173457)

One more thing to check.
If grub is installing to flash drive, do you have a new folder in flash drive /EFI/ubuntu with all the boot files.
The installer just has /EFI/Boot folder, not the /EFI/ubuntu folder.
If you have the /EFI/ubuntu folder then we need to copy it to the NVMe drive.
And that may explain why UUIDs, GUIDs and other settings are wrong as they are the installer's UUID.

You should just be able to use file browser and in / find /EFI and then in /EFI you should just see /Boot. But if also /ubuntu that is where it is installing.

---

### Post by jamespetts on 2017-01-27
I must confess that I am a little confused at this juncture. Apologies if I am missing anything, but GRUB must be installed on the SSD as I get the grub> prompt when I boot from the SSD with the USB drive removed. Also, apart from the steps that I followed a number of posts ago (which did, in fact, install GRUB, albeit it will not actually boot), there is nothing that I have done to try to install GRUB, as all the options to do so in the Boot Repair application are greyed out. Also, the bug report to which you linked seems to refer to a person who us using Secure Boot; are you sure that this is the correct report? My problem seems to be an inability to boot to an existing NVME SSD from a new device that replaced an old failed device of identical specification and an inability to take any steps to restore the boot, which seems different the error reported by this individual.

---

### Post by oldfred on 2017-01-27
I originally posted that bug. It is more related to full installs to sdb or flash drives as grub only installs to sda.
But your flash drive seems to be seen as sda.

Yes, you must have at least part of grub installed. But obviously not all of it.

Was your old drive a NVMe drive?

The way I get my external drives to boot, is just to copy all of /EFI/ubuntu from sda to my external drive. So I was thinking if grub fully installed to your flash drive, then we might be able to copy /EFI/ubuntu from flash drive to NVMe drive.

Does Boot-Repair give any error messages? Never had the issue of greyed out options, other than one or two that do not apply.

So do you have /EFI/ubuntu on flash drive?

---

### Post by jamespetts on 2017-01-28
I do not understand the question about whether my old drive was an NVMe drive; the the SSD that I have in my NUC now is the very same one as was in the old NUC; both it and the RAM were taken from the old broken one before it was sent back and put in the new, working one when it arrived, only the SSD failed (and still fails) to boot for some reason that is still not clear even though the hardware specifications of the new system are identical to the old (even the BIOS revision; there is some possibility that some BIOS settings are different as I cannot recall exactly what the BIOS settings were on the old NUC, and there is no way of finding out now). 

As to the USB drive, I cannot find any /EFI directory: there is a /boot directory with a /grub/ subdirectory, but neither of those contain an EFI directory. The / directory contains initrd.img and vmlinuz. I am not sure whether I am looking in the right place for an /EFI directory, however. 

As to Boot Repair, it does not give any error messages, although it always starts with a notification that it has found a /boot directory (presumably, the one on the USB drive).

---

### Post by oldfred on 2017-01-28
I do not know all the details for a full chroot into LVM & encryption.
You may want to review a standard chroot and then follow the directions on the LVM version, but you have to combine the ones that also mount the ESP - efi system partition. And I expect you have to use your NVMe drive not sdX or sdXY or a mixture with LVM devices.

This is a standard chroot but with an ESP/efi system partition which must also be mounted.
 UEFI chroot
[http://askubuntu.com/questions/53578/can-i-install-in-uefi-mode-with-the-alternate-installer/57380#57380](http://askubuntu.com/questions/53578/can-i-install-in-uefi-mode-with-the-alternate-installer/57380#57380) 
For example it has this:

sudo mount /dev/sda# /mnt            #Mount root (/) partition This has to be the LVM / partition so see below
sudo mount /dev/sda# /mnt/boot       # Your /boot is outside LVM so similar but using NVMe devicesudo mkdir -p /mnt/boot/efi          #Create EFI partition mount point
sudo mount /dev/sda1 /mnt/boot/efi   #Mount EFI partition

I expect you would use instead of above:
# whatever below for LVM
sudo mount /dev/nvme0n1p2 /mnt/boot  
sudo mkdir -p /mnt/boot/efi
sudo mount /dev/nvme0n1p1   /mnt/boot/efi
 
This shows the extra commands you need to mount & unencrypt your LVM, just the first set of steps to the point where it says Resizing Overview.
[https://ubuntuforums.org/showthread.php?p=4530641](https://ubuntuforums.org/showthread.php?p=4530641)
Desktop installer did not include lvm2 & cryptsetup, so if you get error that you have them that is ok.

This may be closer example, but does not have your NVMe drive, but does have efi & LVM.
[http://askubuntu.com/questions/719409/how-to-reinstall-grub-from-a-liveusb-if-the-partition-is-encrypted-and-there-i?rq=1](http://askubuntu.com/questions/719409/how-to-reinstall-grub-from-a-liveusb-if-the-partition-is-encrypted-and-there-i?rq=1)

---

### Post by oldfred on 2017-01-29
Another user with similar LVM, encryption & NVMe drive.

[https://ubuntuforums.org/showthread.php?t=2350963&p=13600757#post13600757](https://ubuntuforums.org/showthread.php?t=2350963&p=13600757#post13600757)

---

### Post by jamespetts on 2017-02-01
I am afraid that I cannot make this work. My output is as follows:

```

To run a command as administrator (user "root"), use "sudo <command>".
See "man sudo_root" for details.

ubuntu@ubuntu:~$ sudo mount /dev/nvme0n1p2 /mnt/boot
mount: mount point /mnt/boot does not exist
ubuntu@ubuntu:~$ mkdir /mnt/boot
mkdir: cannot create directory &#8216;/mnt/boot&#8217;: Permission denied
ubuntu@ubuntu:~$ sudo mkdir /mnt/boot
ubuntu@ubuntu:~$ sudo mount /dev/nvme0n1p2 /mnt/boot
ubuntu@ubuntu:~$ sudo mkdir -p /mnt/boot/efi
ubuntu@ubuntu:~$ sudo mount /dev/nvme0n1p1 /mnt/boot/efi
ubuntu@ubuntu:~$ sudo apt-get update && sudo apt-get install lvm2 cryptsetup
Ign:1 cdrom://Ubuntu 16.04 LTS _Xenial Xerus_ - Release amd64 (20160420.1) xenial InRelease
Hit:2 cdrom://Ubuntu 16.04 LTS _Xenial Xerus_ - Release amd64 (20160420.1) xenial Release
Get:3 http://security.ubuntu.com/ubuntu xenial-security InRelease [102 kB]
Get:4 http://archive.ubuntu.com/ubuntu xenial InRelease [247 kB]                             
Get:6 http://archive.ubuntu.com/ubuntu xenial-updates InRelease [102 kB]                     
Get:7 http://security.ubuntu.com/ubuntu xenial-security/main amd64 Packages [202 kB]
Get:8 http://security.ubuntu.com/ubuntu xenial-security/main Translation-en [85.0 kB]
Get:9 http://security.ubuntu.com/ubuntu xenial-security/main amd64 DEP-11 Metadata [68.0 kB]
Get:10 http://security.ubuntu.com/ubuntu xenial-security/main DEP-11 64x64 Icons [43.1 kB]
Get:11 http://security.ubuntu.com/ubuntu xenial-security/restricted amd64 Packages [6,568 B]
Get:12 http://security.ubuntu.com/ubuntu xenial-security/restricted Translation-en [2,020 B]
Get:13 http://security.ubuntu.com/ubuntu xenial-security/restricted amd64 DEP-11 Metadata [200 B]
Get:14 http://archive.ubuntu.com/ubuntu xenial/main amd64 Packages [1,201 kB]
Get:15 http://archive.ubuntu.com/ubuntu xenial/main Translation-en [568 kB]                  
Get:16 http://archive.ubuntu.com/ubuntu xenial/main amd64 DEP-11 Metadata [733 kB]
Get:17 http://archive.ubuntu.com/ubuntu xenial/main DEP-11 64x64 Icons [409 kB]
Get:18 http://archive.ubuntu.com/ubuntu xenial-updates/main amd64 Packages [460 kB]
Get:19 http://archive.ubuntu.com/ubuntu xenial-updates/main Translation-en [182 kB]
Get:20 http://archive.ubuntu.com/ubuntu xenial-updates/main amd64 DEP-11 Metadata [306 kB]
Get:21 http://archive.ubuntu.com/ubuntu xenial-updates/main DEP-11 64x64 Icons [189 kB]
Get:22 http://archive.ubuntu.com/ubuntu xenial-updates/restricted amd64 Packages [6,568 B]
Get:23 http://archive.ubuntu.com/ubuntu xenial-updates/restricted Translation-en [2,020 B]
Get:24 http://archive.ubuntu.com/ubuntu xenial-updates/restricted amd64 DEP-11 Metadata [157 B]
Fetched 4,914 kB in 1s (3,145 kB/s)                 

** (appstreamcli:3030): CRITICAL **: Error while moving old database out of the way.
AppStream cache update failed.
Reading package lists... Done
Reading package lists... Done
Building dependency tree       
Reading state information... Done
cryptsetup is already the newest version (2:1.6.6-5ubuntu2).
lvm2 is already the newest version (2.02.133-1ubuntu10).
0 upgraded, 0 newly installed, 0 to remove and 575 not upgraded.
ubuntu@ubuntu:~$ sudo modprobe dm-crypt
ubuntu@ubuntu:~$ sudo cryptsetup luksOpen /dev/sda5 crypt1
Device /dev/sda5 doesn't exist or access denied.
ubuntu@ubuntu:~$ sudo cryptsetup luksOpen /dev/nvme0n1 crypt1
Device /dev/nvme0n1 is not a valid LUKS device.
ubuntu@ubuntu:~$ sudo cryptsetup luksOpen /dev/nvme0n1p1 crypt1
Device /dev/nvme0n1p1 is not a valid LUKS device.
ubuntu@ubuntu:~$ sudo cryptsetup luksOpen /dev/nvme0n1p2 crypt1
Device /dev/nvme0n1p2 is not a valid LUKS device.
ubuntu@ubuntu:~$ sudo cryptsetup luksOpen /dev/nvme0n1p3 crypt1
Enter passphrase for /dev/nvme0n1p3: 
ubuntu@ubuntu:~$ sudo vgscan --mknodes
  Reading all physical volumes.  This may take a while...
  Found volume group "ubuntu-vg" using metadata type lvm2
ubuntu@ubuntu:~$ sudo vgchange -ay
  2 logical volume(s) in volume group "ubuntu-vg" now active
ubuntu@ubuntu:~$ sudo mount --bind /dev /mnt/dev
mount: mount point /mnt/dev does not exist
ubuntu@ubuntu:~$ sudo mkdir /mnt/dev
ubuntu@ubuntu:~$ sudo mount --bind /dev /mnt/dev
ubuntu@ubuntu:~$ sudo mkdir /mnt/proc; mkdir /mnt/sys
mkdir: cannot create directory &#8216;/mnt/sys&#8217;: Permission denied
ubuntu@ubuntu:~$ sudo mkdir /mnt/sys
ubuntu@ubuntu:~$ sudo chroot /mnt
chroot: failed to run command &#8216;/bin/bash&#8217;: No such file or directory
ubuntu@ubuntu:~$ apt-get install grub-efi-amd64
E: Could not open lock file /var/lib/dpkg/lock - open (13: Permission denied)
E: Unable to lock the administration directory (/var/lib/dpkg/), are you root?
ubuntu@ubuntu:~$ sudo apt-get install grub-efi-amd64
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following additional packages will be installed:
  grub-common grub-efi-amd64-bin grub-pc-bin grub2-common
Suggested packages:
  multiboot-doc grub-emu xorriso desktop-base
The following packages will be REMOVED:
  grub-gfxpayload-lists grub-pc
The following NEW packages will be installed:
  grub-efi-amd64 grub-efi-amd64-bin
The following packages will be upgraded:
  grub-common grub-pc-bin grub2-common
3 upgraded, 2 newly installed, 2 to remove and 571 not upgraded.
Need to get 3,828 kB of archives.
After this operation, 2,431 kB of additional disk space will be used.
Do you want to continue? [Y/n] 
Get:1 http://archive.ubuntu.com/ubuntu xenial-updates/main amd64 grub2-common amd64 2.02~beta2-36ubuntu3.7 [511 kB]
Get:2 http://archive.ubuntu.com/ubuntu xenial-updates/main amd64 grub-pc-bin amd64 2.02~beta2-36ubuntu3.7 [888 kB]
Get:3 http://archive.ubuntu.com/ubuntu xenial-updates/main amd64 grub-common amd64 2.02~beta2-36ubuntu3.7 [1,705 kB]
Get:4 http://archive.ubuntu.com/ubuntu xenial-updates/main amd64 grub-efi-amd64-bin amd64 2.02~beta2-36ubuntu3.7 [658 kB]
Get:5 http://archive.ubuntu.com/ubuntu xenial-updates/main amd64 grub-efi-amd64 amd64 2.02~beta2-36ubuntu3.7 [66.1 kB]
Fetched 3,828 kB in 0s (5,389 kB/s)       
Preconfiguring packages ...
(Reading database ... 191100 files and directories currently installed.)
Removing grub-gfxpayload-lists (0.7) ...
Removing grub-pc (2.02~beta2-36ubuntu3) ...
Processing triggers for man-db (2.7.5-1) ...
(Reading database ... 191080 files and directories currently installed.)
Preparing to unpack .../grub2-common_2.02~beta2-36ubuntu3.7_amd64.deb ...
Unpacking grub2-common (2.02~beta2-36ubuntu3.7) over (2.02~beta2-36ubuntu3) ...
Preparing to unpack .../grub-pc-bin_2.02~beta2-36ubuntu3.7_amd64.deb ...
Unpacking grub-pc-bin (2.02~beta2-36ubuntu3.7) over (2.02~beta2-36ubuntu3) ...
Preparing to unpack .../grub-common_2.02~beta2-36ubuntu3.7_amd64.deb ...
Unpacking grub-common (2.02~beta2-36ubuntu3.7) over (2.02~beta2-36ubuntu3) ...
Selecting previously unselected package grub-efi-amd64-bin.
Preparing to unpack .../grub-efi-amd64-bin_2.02~beta2-36ubuntu3.7_amd64.deb ...
Unpacking grub-efi-amd64-bin (2.02~beta2-36ubuntu3.7) ...
Selecting previously unselected package grub-efi-amd64.
Preparing to unpack .../grub-efi-amd64_2.02~beta2-36ubuntu3.7_amd64.deb ...
Unpacking grub-efi-amd64 (2.02~beta2-36ubuntu3.7) ...
Processing triggers for man-db (2.7.5-1) ...
Processing triggers for install-info (6.1.0.dfsg.1-5) ...
Processing triggers for ureadahead (0.100.0-19) ...
Processing triggers for systemd (229-4ubuntu4) ...
Setting up grub-common (2.02~beta2-36ubuntu3.7) ...
update-rc.d: warning: start and stop actions are no longer supported; falling back to defaults
Setting up grub2-common (2.02~beta2-36ubuntu3.7) ...
Setting up grub-pc-bin (2.02~beta2-36ubuntu3.7) ...
Setting up grub-efi-amd64-bin (2.02~beta2-36ubuntu3.7) ...
Setting up grub-efi-amd64 (2.02~beta2-36ubuntu3.7) ...
ubuntu@ubuntu:~$ grub-install --recheck --no-floppy --force
Installing for x86_64-efi platform.
grub-install: error: cannot find EFI directory.
ubuntu@ubuntu:~$ 

```

If I have done something wrong with this, I am afraid that it is not clear from the above what it is. 

I am afraid that I really do not have time to continue to attempt to make this work, and I will have to reformat and reinstall from scratch.

---

### Post by The Cog on 2017-02-01
You have to be working as root to have permission to create /mnt/boot:
```
sudo mkdir /mnt/boot
```

---

### Post by oldfred on 2017-02-01
It looks like you had grub-pc for BIOS boot even though otherwise configured for UEFI boot.
And that is why you have been getting grub boot errors.

Do not understand why this error unless it still is trying to install to sda.
grub-install: error: cannot find EFI directory.

And the link I posted above was another user with NVMe & LVM, so it must work if the correct magic incantation is given.

---

### Post by LostFarmer on 2017-02-01
What site did you use for instructions ?  The way you did the commands is not correct.  the below is verified on a debian install and with a mint lvm and encrypted. the 2 [SIZE=2](/dev/ubuntu-vg/root) could be wrong but the output of  [/SIZE][SIZE=2]lvscan will show if it is correct.[/SIZE]



```
[SIZE=2]sudo -i                 *         (small I) -puts terminal into root where sudo will not be needed till closed.

  apt-get update &&  apt-get install lvm2 cryptsetup                                * not needed-cryptsetup is already the newest version 
  modprobe dm-crypt
  cryptsetup luksOpen /dev/nvme0n1p3 crypt1                                *REQUESTS passphrase
  vgscan
  vgchange -ay
  lvscan
(You now must mount ubuntu-vg to /mnt) 
  mount /dev/ubuntu-vg/root /mnt                           *:does the output of lvscan have "/dev/ubuntu-vg/root" if not change to lvscan

  mount /dev/nvme0n1p2 /mnt/boot
  mount /dev/nvme0n1p1 /mnt/boot/efi
  mount --bind /dev /mnt/dev 
  mount --bind /dev/pts /mnt/dev/pts
  mount --bind /proc /mnt/proc
  mount --bind /sys /mnt/sys
  cp /etc/resolv.conf /mnt/etc/
  chroot /mnt
  apt-get install --reinstall grub-efi-amd64
  update-grub

  umount /dev/nvme0n1p1
  umount /dev/nvme0n1p2
  umount /dev/ubuntu-vg/root                **(see note above for lvscan output)
  vgchange -an  
  cryptsetup luksClose crypt1[/SIZE]
```

---

### Post by oldfred on 2017-02-02
Thanks LostFarmer.
I was trying to help OP, but only had links to standard chroot, a UEFI chroot and mounting of LVM partitions. I do not really know LVM & encryption, and could not correctly combine them. I hoped OP could combine them, but your instructions are much clearer. (bookmarked for future reference.)

---

### Post by LostFarmer on 2017-02-02
oldfred-- just install a lvm with  encryption on external hdd on Sat. , 2nd attempt my crappy key pad selected the internal hdd, and a new partition table was written.  Have recovered all the partitions but Win8.1 (data was written for the lvm partition to it) is shot but I have win10 home and pro- no loss.  I had to read many different sites on mounting a lvm with encryption before I was able to put together the commands that worked,  I did not try chroot'ing so not 100% those commands are right ( I only tried to chroot a couple times in the past 10 years and it never worked).

This site was the best for mounting but it is for Mint> [https://forums.linuxmint.com/viewtopic.php?f=50&t=198706&p=1043424&hilit=mount+lvm#p1043424](https://forums.linuxmint.com/viewtopic.php?f=50&t=198706&p=1043424&hilit=mount+lvm#p1043424)  .  it does not have correct commands to umount .

---

