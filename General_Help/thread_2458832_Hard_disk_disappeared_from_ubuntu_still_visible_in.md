---
title: "Hard disk disappeared from ubuntu still visible in Win 7 dual boot"
date: 2021-03-04
forum: General Help
---

### Post by mitch beedie on 2021-03-04
Hello &#8211; help appreciated

I inadvertently clicked a &#8220;Restore disk image&#8221; pop-up window and now one of my hard disks seems to have disappeared. I was installing a Raspberry Pi Naturewatch camera installation program and the D: drive (sdc) seems to have been replaced by &#8216;boot&#8217; and &#8216;rootfs&#8217; (both related to Naturewatch) in Other Locations>On This Computer. 

I&#8217;m dual booting Ubuntu with Windows7 and the drive is visible from Windows, which showed an empty disk which allowed me to copy a file to it. The relevant items of an lshw listing seem to be: 


```
/0/3/0.0.0         /dev/sdc   disk           1TB WDC WD10EARX-00N [this is not visible] 
/0/3/0.0.0/1       /dev/sdc1  volume         43MiB Windows FAT volume
/0/3/0.0.0/2       /dev/sdc2  volume         4241MiB EXT4 volume
    
/0/5/0.0.0         /dev/sdd   disk           1TB WDC WD10EZRX-00A
/0/5/0.0.0/1       /dev/sdd1  volume         931GiB Extended partition
/0/5/0.0.0/1/5     /dev/sdd5  volume         931GiB Windows NTFS volume [this is the one that is visible] 
 
... and ... 

Disk /dev/sdb: 223.6 GiB, 240057409536 bytes, 468862128 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disklabel type: dos
Disk identifier: 0x7b0ad8dd

Device     Boot  Start       End   Sectors   Size Id Type
/dev/sdb1  *      2048    206847    204800   100M  7 HPFS/NTFS/exFAT
/dev/sdb2       206848 468858879 468652032 223.5G  7 HPFS/NTFS/exFAT


Disk /dev/sdc: 931.5 GiB, 1000204886016 bytes, 1953525168 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes
Disklabel type: dos
Disk identifier: 0x667b56cc

Device     Boot Start     End Sectors  Size Id Type
/dev/sdc1        8192   96453   88262 43.1M  c W95 FAT32 (LBA)
/dev/sdc2       98304 8783871 8685568  4.1G 83 Linux


Disk /dev/sdd: 931.5 GiB, 1000204886016 bytes, 1953525168 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes
Disklabel type: dos
Disk identifier: 0xa69d1928

Device     Boot Start        End    Sectors   Size Id Type
/dev/sdd1        1985 1953519615 1953517631 931.5G  f W95 Ext'd (LBA) 
/dev/sdd5        2048 1953519615 1953517568 931.5G  7 HPFS/NTFS/exFAT 

Partition 1 does not start on physical sector boundary.

```

Is the drive just unmounted? And how can I get it back &#8211; anyone know? 

Thanks

---

### Post by oldfred on 2021-03-05
Copying to it may have been a mistake as it overwrote something.

What does testdisk show for sdc drive?
It looks like you may have installed your Nature Watch to drive totally overwriting it.

If deeper search shows files you want to recover, immediately copy them to another drive. You may not get them again.

download TestDisk, in most Linux repositories, so you can also download from anUbuntu install.
 [http://www.cgsecurity.org/wiki/TestDisk](http://www.cgsecurity.org/wiki/TestDisk)
Testdisk Instructions, new versions use sectors, old ones were CHS
[http://www.cgsecurity.org/wiki/TestDisk_Step_By_Step](http://www.cgsecurity.org/wiki/TestDisk_Step_By_Step)
[http://www.cgsecurity.org/wiki/Menu_Analyse](http://www.cgsecurity.org/wiki/Menu_Analyse)

---

### Post by mitch beedie on 2021-03-05
Thank you :) I shall go off and give that a study.

---

### Post by mitch beedie on 2021-03-13
Thanks again, this looks promising. Sorry about the delay - I had problems getting into Testdisk (actually very simple, caused by my terminal stupidity). 

I had all my data backed up so no problem there. The disk shows up fine, when I look it says: 

Current partition structure:
     Partition                  Start        End    Size in sectors

Warning: number of heads/cylinder mismatches 64 (FAT) != 255 (HD)
Warning: number of sectors per track mismatches 32 (FAT) != 63 (HD)
 1 P FAT32 LBA                0 130  3     6   1  1      88262 [boot]
 2 P Linux                    6  30 25   546 196 34    8685568 [rootfs]
No partition is bootable

so is showing up the boot and rootfs that display on On This Computer. As you say, I've installed the program onto that disk which wasn't the intention at all :( 

Any further thoughts?

---

### Post by oldfred on 2021-03-13
You may need chkdsk from Windows on the FAT32 partition.
Or dosfsck on the FAT32 partition from Linux.

Must be unmounted
sudo dosfsck -t -a -w /dev/sdc1
The -a seems to help in clearing dirty bit
[https://bbs.archlinux.org/viewtopic.php?id=164185](https://bbs.archlinux.org/viewtopic.php?id=164185)

If that was your Linux drive, you need to totally reinstall & restore from backups.

You also show MBR(msdos) partitions on all drives. I now only suggest MBR, for those with older systems that have to boot Windows.
Windows requires MBR for BIOS boot & requires gpt for UEFI boot. Ubuntu can boot from gpt drives with either BIOS or UEFI, if you have correct supporting partitions for booting. With BIOS, you need a bios_grub, 1MB unformatted or an ESP - efi system partition, FAT32 3000 to 500MB with esp & boot flags.
[http://www.rodsbooks.com/gdisk/whatsgpt.html](http://www.rodsbooks.com/gdisk/whatsgpt.html)

---

### Post by mitch beedie on 2021-03-14
From Linux dosfsck I get: 

fsck.fat 4.1 (2017-01-24)
/dev/sdc1: 170 files, 44282/86872 clusters

When you say was that your Linux drive do you mean did it boot from that drive? If so, no - it was just a data drive and I have backup. 

Not sure how to do a reinstall from Linux. Could I go into Windows and format the drive since it's visible as a single drive there? I'll copy all its previous contents across no problem. Otherwise I'm not sure how I'd reinstall other than format from Linux (I didn't actually set up the dual-boot on the computer, a friend did it) . Should I format in NTFS or FAT32 or ext-4 (I only really need to access it from linux)? With something like unmount it and do a

sudo mkfs -t ntfs /dev/sdc1

You're scaring me with MBR and gpt :( I'm very basic and reluctant to change anything fundamental in case I screw it all up. I mainly use the computer for word processing/spreadsheet/browsing/e-mails with the odd bit of graphics, and it does work well when I don't mess up installing new software (sorry :( and help definitely appreciated).

---

### Post by oldfred on 2021-03-14
I have been using gpt since 2010. I converted one drive to gpt and installed Ubuntu. Other drive was still MBR with XP.
Once I retired XP, I started converting all new or totally repartitioned drives to gpt. 
Not sure I would suggest converting in place unless you have good backup. And you should have good backups anyway.

I also suggest only using Windows tools for Windows and use Linux tools for Linux.
If you are going to reinstall, you do not have to reformat as ext4 as you do that during install. Only if converting may you then have to create new partitions.

Only use NTFS if you have Windows. Otherwise use ext4 for Linux.
The FAT32 is only used with newer UEFI systems for the ESP- efi system partition used for UEFI booting.
Mixing UEFI & BIOS is not recommended, unless advanced user and wanting to experiment.

---

### Post by mitch beedie on 2021-03-15
Thanks again - can I summarize/check? 

sda is a 120 Gb internal SSD which boots to linux 
sdb is a 240 Gb internal SSD which boots to Windows7 (dos) 

I&#8217;m reluctant to reinstall linux if it would affect these two, since both of them work really well (not a huge amount of free space on the linux SSD but I can live with that).  The other three are hard disks:  

sdc is a 1 Tb internal hard disk that was called Data that I held all my personal/work information on (dos) that is now wiped 
sdd is a 1 Tb internal hard disk that is called  Backup disk that backs up Data (dos) 
sde is a 1 TB external hard disk that also backs up Data 

I&#8217;m really not sure how I&#8217;d go about reinstalling the whole system - can I really not unmount sdc and do: 

sudo mkfs.ext4 /dev/sdc1 (sdc1 rather than just sdc?) to format just that hard drive if it needs to be ext4? 

sorry to be a pain

---

### Post by oldfred on 2021-03-15
You create partitions on a drive, then format partitions.

I normally use gparted for both, but then using Something Else typically end up formatting it as ext4 again.
If multiple drives only use Something Else to install.

And grub in BIOS mode defaults to installing grub to first drive, usually sda, or first NVMe drive, but with BIOS you can choose if you use Something else using the combo box for boot loader install drive.

If UEFI Ubuntu's Ubiquity installer only installs grub to first drive, even though it still shows the options on where to install.
I do prefer to then have install on first drive. That typically is determined by BIOS/UEFI by SATA port, or sda is SATA0, sdb is SATA1, etc.
But when I plug in a flash drive that is sdf, on reboot if still plugged in, it becomes sda and every other drive changes up one letter. That is why UUID or labels are used to know which drive is which for fstab and other entries.

---

### Post by mitch beedie on 2021-03-19
Well that went well :) . 

I edited fstab and then the computer didn&#8217;t boot any more. When I booted I was asked for the root password which hadn&#8217;t been set. I tried setting it using a live ubuntu usb and it seemed to work but then didn&#8217;t. But anyway. 

I&#8217;ve installed ubuntu 20.04 on sdd (sata 3, 1 TB hard disk) from a live usb because I&#8217;ve been meaning to do that for a while and that seemed the only disk with enough space. I&#8217;ve recovered nearly everything from the old setup (must say I&#8217;m impressed with how easy it is to recover thunderbird and firefox settings and information). I&#8217;ve ordered a new 240MB SSD and 2 TB hard disk because both drives were getting a bit full anyway. 

So the plan is to 
1) take out the 120 MB ssd from sda (sata 0), insert my new 240MB ssd, install 20.04 on it, and copy my thunderbird and firefox (etc) personal data to it 
2) leave sdb (sata 1) alone and hope that I will be able to still boot into Win7 from it,
3) then (unless this isn&#8217;t a good idea) I&#8217;d ideally physically move the 1 TB hdd (sata 3) cable to the sata 2 socket to become my main 1TB data hard drive, and format it to remove the ubuntu 20.04 now installed,  
4) insert the new 2TB hard disk to become sata 3 as backup, 
5) copy all my data to the 1TB sdc hard drive, and back it up on the new 2TB sdd hard drive. 

&#8230;. and breathe&#8230; 

Does this make sense, and if I&#8217;m reinstalling sda from a live ubuntu usb will that solve the MBR problems you highlighted above? I have another computer I can use the old SSD and hard disk on so they won&#8217;t be wasted. 

I&#8217;m hoping the new sda drive will recognize the other drives. I&#8217;m a bit confused as to why the new ubuntu installation on sdd still doesn&#8217;t see sdc, but hopefully reinstalling sda with a live ubuntu usb will solve this.

---

### Post by oldfred on 2021-03-19
With a totally new drive, I really suggest using gpt.
But with gpt, you must have either a 1MB unformatted partition with bios_grub flag (if using gparted) or an ESP - efi system partition as FAT32 about 300 to 500MB. When first planning conversion to new UEFI system, I had both bios_grub & ESP on new drives.

For the Total space you want for Ubuntu:
Ubuntu's standard install is just / (root) & swap(prior to 17.10), but it is better to add another partition for /home if allocating over 30GB.:
Only if gpt -  all partitions in gpt are primary (no logicals):
gpt: 300-500 MB efi FAT32 w/boot flag (ESP for UEFI boot or future use for UEFI, you only can have one per drive, so if already existing do not attempt another)
gpt: 1 or 2 MB No Format w/bios_grub flag (for BIOS boot not required for UEFI)
for gpt(GUID) or MBR(msdos) partitioning
Ubuntu partitions - smaller root only where hard drive space is limited.
If total space less than about 30 to 50GB just use / not separate /home or standard install.
1. 30+ GB Mountpoint / primary or logical beginning ext4
2. all but 2 GB or all (See below if 18.04 or later) Mountpoint /home logical beginning ext4
3. 2 GB Mountpoint swap logical (not required with 17.04 and later uses a swap file, if no swap partition found)
4. You do not need to create swap, as it either finds existing swap partition, or creates in fstab the following swapfile entry:
5. No swap partition for 18.04 or later, it uses a swap file like this entry in fstab:
     /swapfile                                 none            swap    sw              0       0

Discussion of swapfile vs swap partition, many suggest swap partition.
[https://ubuntuforums.org/showthread.php?t=2458900](https://ubuntuforums.org/showthread.php?t=2458900)

sudo parted /dev/sda mklabel gpt
Above label is partition type, not partition label.


I normally use gparted to create gpt & partitions.
You can also use gparted but must change default partitioning first.
Select gpt under device, advanced over msdos(MBR) default partitioning before starting.
Or use gdisk which is in repository, now standard in newer installs:

---

### Post by mitch beedie on 2021-04-01
I've run through your previous answers again and done some reading and hope I’m prepared. I’m planning to: 

1) back up recent files , thunderbird, firefox & Windows 7 , 
2) delete partitions and change MBR to GPT disk in Windows disk management, (format sdb1 as ntfs  100MB, format sdb2 as ntfs 239900MB, label windows 7) and reinstall Win7 on sdb.
3) physically replace sda (ubuntu boot disk) with new ssd in slot 0, leave sdb (Windows boot disk) in slot 1, move 1 TB hard disk (data) to slot 2, add new 2 TB hard disk (backup) to slot 3
4) reinstall Win7
5) download updates in ubuntu startup screen, unmount and delete partitions for all drives using Something Else, 
6) click New partition table, specify UEFI with Gpt partition table from dropdown menu
7) for each drive move to space and press +, add Primary partition (at the beginning of space), format partitions (tick Format boxes) with structure as follows:

sda (label: ubuntu 18.04 - not keen on 20.04 yet because no drag and drop on desktop plus files disappear from desktop itself even though they stay in the Desktop file) 
dev/sda1: format as FAT32 /boot 512MB (prompted to install grub bootloader)
dev/sda2: format as swap /swap 16000MB (for 8 GB RAM (primary partition) 
dev/sda3: format as ext4 / 79000MB primary (root)  partition gpt 
dev/sda4: format as ext4  /home 145500MB primary (i.e. rest of disk)  

sdb set up using Windows software above 

sdc (label: adata)
	dev/sdc1 format as ntfs 1Tbyte (single partition only) 

sdd (label: backup)
	sdd1 format as ntfs 2 Tbyte (single partition only) 

look ok?

---

### Post by oldfred on 2021-04-01
How you boot install media, UEFI or BIOS is then how it installs.
The Windows 7 installer may be UEFI or not. Early versions were not, had to be copied to flash drive & some files moved & renamed to have the UEFI Windows boot files. Newer release of Windows 7 included those updates, but you still had to boot installer in UEFI mode.
Windows in UEFI mode want multiple additional partitions. Best to let it create its partitions and then only manually use gparted to create Linux partitions.
[https://docs.microsoft.com/en-us/windows-hardware/manufacture/desktop/configure-uefigpt-based-hard-drive-partitions#RecommendedPartitionConfigurations](https://docs.microsoft.com/en-us/windows-hardware/manufacture/desktop/configure-uefigpt-based-hard-drive-partitions#RecommendedPartitionConfigurations)

Still best not to use Windows 7 as it is EoL - End of Life.

Note that drive like sda will change depending on which SATA port you plug a drive into. Usually SATA0 is sda or in grub hd0 as no drive has been mounted before boot. And when rebooting I have had my USB flash drive become sda and then every other drive moves up a letter. Do not depend on device like /dev/sda. And if using device always check first that you are using correct one.

UEFI often forgets UEFI boot entry when a drive is unplugged. Many auto find Windows in an ESP with /EFI/Microsoft but few find any other system.
You can easily use efibootmgr to add/replace an UEFI entry or reinstall boot loader. UEFI also boots /EFI/Boot/bootx64.efi which is a fallback or drive boot entry. That is same path as external devices. With a Windows install bootx64.efi is a copy of Windows .efi boot file. With Ubuntu, now bootx64.efi is a copy of shimx64.efi or grubx64.efi to boot Ubuntu. Old versions did not create that folder & file. If installing Windows & Ubuntu in one drive bootx64.efi gets overwritten. May be either Windows or shimx64.efi. Boot-Repair backs it up and copies shimx64.efi to it, from when grub did not create bootx64.efi.

---

### Post by mitch beedie on 2021-04-01
> How you boot install media, UEFI or BIOS is then how it installs.
The Windows 7 installer may be UEFI or not. Early versions were not, had to be copied to flash drive & some files moved & renamed to have the UEFI Windows boot files. Newer release of Windows 7 included those updates, but you still had to boot installer in UEFI mode.

I&#8217;ve backed up Win7 to flash drive with UEFI using AOMEI Partition Assistant, am hoping that will be ok. 

> Windows in UEFI mode want multiple additional partitions. Best to let it create its partitions and then only manually use gparted to create Linux partitions.
[https://docs.microsoft.com/en-us/win...Configurations](https://docs.microsoft.com/en-us/win...Configurations) 

Am planning to let Windows in UEFI mode to install itself (original Win7 disk/AOMEI flash drive backup - have multiple drives so using Something Else method for creating Linux partitions as you suggested?  

> Still best not to use Windows 7 as it is EoL - End of Life.

Yes true Win7 is out of date. I saw what Microsoft did to Win8 and hated it with a passion (loads of &#8216;apps&#8217; that seem to want you to buy things for no apparent reason, nasty nasty). Win10 seemed similar and had so many problems when it was introduced that I didn&#8217;t bother. Since then I&#8217;ve used Win7 happily, I&#8217;ve just disabled access to the web since all I use it for is Word when I get a work document with a lot of complicated Track Changes, which isn&#8217;t often. I just copy a document across from ubuntu, work on it, and copy it back to ubuntu with no web access. 

Hoping not having to pay to upgrade to Win10 with attendant hassles. I&#8217;m not actually convinced it is problem free yet:  [https://www.product-reviews.net/down/windows-10-update-problems/](https://www.product-reviews.net/down/windows-10-update-problems/) So if I can I&#8217;d like to keep Win7, just not connect it to the web. I&#8217;ve got my original Win7 disk but not sure what year it was though (possibly 2012). 

> Note that drive like sda will change depending on which SATA port you plug a drive into. Usually SATA0 is sda or in grub hd0 as no drive has been mounted before boot. And when rebooting I have had my USB flash drive become sda and then every other drive moves up a letter. Do not depend on device like /dev/sda. And if using device always check first that you are using correct one.
 

I was hoping that giving labels to the drive would solve this? I could give the drive identifiers if labels won't work ok. 

> UEFI often forgets UEFI boot entry when a drive is unplugged. Many auto find Windows in an ESP with /EFI/Microsoft but few find any other system. You can easily use efibootmgr to add/replace an UEFI entry or reinstall boot loader. UEFI also boots /EFI/Boot/bootx64.efi which is a fallback or drive boot entry. That is same path as external devices. With a Windows install bootx64.efi is a copy of Windows .efi boot file. With Ubuntu, now bootx64.efi is a copy of shimx64.efi or grubx64.efi to boot Ubuntu. Old versions did not create that folder & file. If installing Windows & Ubuntu in one drive bootx64.efi gets overwritten. May be either Windows or shimx64.efi. Boot-Repair backs it up and copies shimx64.efi to it, from when grub did not create bootx64.efi. 

Won&#8217;t be unplugging any of the main four drives sata0 to sata3. Not installing on a single drive &#8211; one for ubuntu and one for Windows. Don&#8217;t really understand the rest, sorry, am hoping I can come back to it if I have problems :(

---

### Post by oldfred on 2021-04-01
I like to have the 4 main apps I use as icons in top menu bar.
I used fallback/flashback when Ubuntu switched from old gnome2. Flashback was similar to old gnome3.
It was then suggested to try Kubuntu. I found it very similar, so things in different places. But I have icons in top bar as I like.
It seems more configurable, but sometimes finding those settings is a learning experience as bit different.
Easier than Windows.

My last real Windows was XP. I barely used Windows 7.
I do have one system with Windows 10, originally 8. It just for watching video that does not work with Ubuntu.
I find I have to look up to make even minor changes. Often Internet has some slightly different version and menu drill down is different. But once I get to lowest level where I make change, I think it is still same screens as XP was.

---

### Post by mitch beedie on 2021-04-02
Interesting, ta.  (I also looked up efibootmgr which could be very useful). 

I did use XP but don't remember it. The thing I like about Win7 is that it was rock solid - pretty much like my experience of ubuntu. 

I'll have a go at reinstalling things tonight. If I can't reinstall Win7 it won't be too dramatic. I've heard you can run it in a virtual machine on ubuntu, but I've resisted because I did try running Wine and it repeatedly fell over. I could give that a go though - I still have my original Microsoft Office disks in case I need them. 

Whatever happens thanks for all your time, I've learned loads from this (largely not to install software onto my hard disk by mistake, admittedly).

---

### Post by mitch beedie on 2021-04-02
Grrr double post

---

### Post by dragonfly41 on 2021-04-02
If you are still wedded to old Windows 7 can you not try installing a VM for Win 7 inside **VirtualBox **inside host Ubuntu[B]?
[/B]VirtualBox is not Wine. Problem is you need healthy RAM size.

---

### Post by mitch beedie on 2021-04-02
Thanks, yes, I'll try to install Win7 but if it doesn't work I'll certainly give VirtualBox a go.

---

### Post by mitch beedie on 2021-04-11
Bit of a delay again, I was waiting for delivery of an external backup disk and then it took me a while fiddling. It&#8217;s all working again (touch wood) after a large number of reboots and Repair Disk reboots and messing with Something Else and gparted and BIOS boot screens. 

Wouldn&#8217;t let me use FAT32 for boot partition, told me I needed (as I recall) ext2 so I did that. I&#8217;m now using UEFI/gpt  but decided against dual Windows boot, I&#8217;ll try Virtual Box on my spare SSD. 

So thanks again &#8211; not sure I can mark thread as &#8216;Solved&#8217; since I wouldn&#8217;t suggest people go through all this including my mistakes to reinstate a hard drive. Perhaps for reinstalling complete ubuntu system using gpt rather than MBR, though.

---

### Post by oldfred on 2021-04-11
Do not mix an ESP which does have boot files for UEFI booting, and has to be FAT32 with a /boot partition which has to have a Linux format for kernel & boot files.

Most desktops do not need a separate /boot partition, but some server type installs or LVM with encryption may want a /boot partition.

---

### Post by mitch beedie on 2021-04-11
Ah well - I've got a Linux format /boot partition plus / and /swap and /home partitions, seems to work ok.

---

