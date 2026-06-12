---
title: "Install Ubuntu On Separate SSD (and be able to boot to it an Win7)"
date: 2018-07-01
forum: General Help
---

### Post by tazmo8448 on 2018-07-01
I have a notebook (yep HP) and have a buyer that after I installed a 'fresh' Win7 OS wants the other SSD to have Ubuntu installed. I'm finding (using all sorts of YouTube videos) that when Ubuntu is installed on the separate drive that Win7 defaults to the Win7 OS and when going to Computer an looking at the extra drive (in this case E:\) it is listed as empty and upon clicking on it get a warning that to access this it has to be reformatted which sounds correct because it now has Ubuntu on it that Win7 can't 'see.' 
Is there a file or something that I can insert in Win7 to 'see' Ubuntu? 

Not really wanting to create a partition on the OS drive to put Ubuntu on when I have another empty SSD installed.

Any help would very appreciated.

Thanks,

Sam

---

### Post by oldfred on 2018-07-01
Is computer UEFI or BIOS.
Did you install Windows 7 in BIOS or UEFI boot mode?
Note that default install of Windows 7 from DVD is the 35 year old BIOS/MBR configuration and must be converted to a flash drive and a couple of files moved & renamed to make it UEFI bootable.
Windows only boots in BIOS mode from MBR(msdos) partitioned drive.
Windows only boots in UEFI boot mode from gpt partitioned drives. So difficult to convert after install.
       BIOS & UEFI Windows partitions, note system has totally different format  & meaning between BIOS & UEFI
[https://msdn.microsoft.com/en-us/library/windows/hardware/dn898504%28v=vs.85%29.aspx](https://msdn.microsoft.com/en-us/library/windows/hardware/dn898504%28v=vs.85%29.aspx) & 
[https://msdn.microsoft.com/en-us/library/windows/hardware/dn898510%28v=vs.85%29.aspx#RecommendedPartitionConfigurations](https://msdn.microsoft.com/en-us/library/windows/hardware/dn898510%28v=vs.85%29.aspx#RecommendedPartitionConfigurations) 

If Windows is BIOS, then you really have to install Ubuntu in BIOS boot mode. If Ubuntu on its own drive, I would still use gpt partitioning, as Ubuntu can boot from gpt with either UEFI or BIOS. And if you have both the ESP & bios_grub as first two partitions, you can easily convert later from one boot mode to the other.

Either way, you need to use Something Else install option, or disconnect Windows drive. And how you boot install media UEFI or BIOS is then how it installs.

       For the Total space you want for Ubuntu:
Ubuntu's standard install is just / (root) & swap(prior to 17.10), but it is better to add another partition for /home if allocating over 30GB.:
Only if gpt -  all partitions in gpt are primary (no logicals):
gpt: 300-500 MB efi FAT32 w/boot flag (ESP for UEFI boot or future use for UEFI, you only can have one per drive, so if already existing do not attempt another)
gpt: 1 or 2 MB No Format w/bios_grub flag (for BIOS boot not required for UEFI)
for gpt(GUID) or MBR(msdos) partitioning
Ubuntu partitions - smaller root only where hard drive space is limited.
If total space less than about 30 to 50GB just use / not separate /home or standard install.


[LIST=1]
[*]25-30+ GB Mountpoint / primary or logical beginning ext4
[*]all but 2 GB Mountpoint /home logical beginning ext4
[*]2 GB Mountpoint swap logical (not required with 17.04 and later uses a swap file, if no swap partition found) or system will create this in fstab:
[*]/swapfile                                 none            swap    sw              0       0
[/LIST]

---

### Post by yancek on 2018-07-01
If you are using the windows 7 default of a Legacy install, your situation could be explained by your install the Ubuntu Grub bootloader to the Ubuntu partition rather than the MBR of that drive.  You could also install to the MBR of the windows drive but that depends upon what is wanted, separately bootable drives you need Grub on the same drive as the SSD for Ubuntu.

 > when going to Computer an looking at the extra drive (in this case E:\

That's surprising as windows does not usually give drive letters to non-windows systems.

Boot Linux from windows, yes you can.  See the link below.  You'll need your Ubuntu Live DVD or flash drive.

 [https://www.iceflatline.com/2009/09/how-to-dual-boot-windows-7-and-linux-using-bcdedit/](https://www.iceflatline.com/2009/09/how-to-dual-boot-windows-7-and-linux-using-bcdedit/)

Answering the questions posed above should go a long way toward getting help, particularly whether UEFI or Legacy install.

---

### Post by tazmo8448 on 2018-07-01
Both SSD's are 128 GB Win7 takes about 20 GB at this point...so what you're saying if I read you correctly is to take out the WinOS drive put the Unbuntu drive in the Primary bay or slot boot to it an let it create itself then add those partitions inside Ubuntu to have space for the /home deal....
I do know that when installing Win7 recently I had a small HP program that converted the system to an efi based BIOS...basically I re-flashed the BIOS prior to installing the OS with it.

Looking at Disk Manager I'm showing both drives as GPT types and the OS has the usual 100 mb partition reserved with 28.1 mb in use with the other 71.8 showing as free space.....which leads me to believe that it is the regular MBR partition type. There is no 'recovery' or any other partition on the Win7 OS drive. I'm thinking my Win7 OS is gpt an it uses an efi boot...but not sure really.

---

### Post by tazmo8448 on 2018-07-01
no I've found that when plugging in a USB or External drive windows immediately assigns a letter.....and as said before the secondary SSD (blank btw) connected internally shows the drive letter E:\ and is listed as a Data Drive....C:\ drive with the OS is listed as the OS Drive....I have several external hard drives an each time I plug one in to a USB port or connect it internally it is ALWAYS assigned a letter...don't understand why that was found to be surprising.
I do have a Unetbootin bootable usb created and I also have a LIVEUSB created (w/persistence) but the new buyer would like to have both the LiveUSB & Ubuntu on the secondary drive...

I'm almost positive the Win7 OS is a legacy boot system as it was made in 2010 and I purchased it new in late 2011 (HP dv7-4177nr)

If I'm understanding what you are saying you say to make sure the Grub thing is up an running on the Ubuntu drive....

let me say this....I searched youtube found some tutorials and followed them to the complete install of Ubuntu but upon restart (as required) Ubuntu failed to show up and the drive it was on was rendered unaccessable....so basically I'm starting all over from scratch again.

---

### Post by oldfred on 2018-07-01
Since Windows is partitioning dependant, we can see which way it has installed.
Some vendors used a FAT32 partition as recovery. These were often the systems just before Microsoft required UEFI/gpt.

Post this from Ubuntu in live boot mode:
sudo parted -l

If a laptop with DVD bay as second drive, you need to check if you can boot from it. Some can only use it as a data drive or as the DVD.

---

### Post by tazmo8448 on 2018-07-01
My notebook shows as Boot Options:- 

Notebook Hard Drive

Internal CD/DVD ROM Drive

Any USB if inserted

the issue i'm having is in trying to install Ubuntu; then when the time comes to restart as instructed all is lost....I did put it on the empty drive I did use the ( / ) method of installing I did not ask or enter any other commands before installing such as /home or anything else. That may be the issue. So...when the install is finished I don't have a chance to go to the Terminal to issue any commands...it only wants a 'restart' to finish the install which as said ends up dead in the water.

---

### Post by tazmo8448 on 2018-07-01
I do have a bootable usb with Ubuntu 18.04 Mate and I also have a LiveUSB with 18.04 Mate (w/persistence) I'm thinking I need to take out the Win7 drive swap it with the blank drive then put Ubuntu on that and hopefully get the Grub thing installed on it then shut it all down swap the drives again an see if they both show as options on Startup......

---

### Post by tazmo8448 on 2018-07-01
After all the hassle I am just going to use a large USB an create a LiveUSB and use that rather than going thru all the pains of creating Ubuntu on a separate internal hard drive...

I want to thank ALL you good people  oldfred  &  yancek  for taking the time an making the effort....it was truly appreciated....&#55357;&#56397;

---

### Post by tazmo8448 on 2018-07-01
btw the two question marks in diamonds was a thumbs up.....

---

