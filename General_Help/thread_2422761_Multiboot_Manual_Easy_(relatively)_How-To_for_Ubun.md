---
title: "Multiboot Manual Easy (relatively) How-To for Ubuntu"
date: 2019-07-12
forum: General Help
---

### Post by vidtek on 2019-07-12
I have been searching for a while now to make a UEFI-only booting USB stick, I have tried all the various programmes out there, multibootusb, Multiboot, Yumi and not one of them either works as advertised or has other limitaions that I found troubling.

I have scoured the various forums and gleaned little bits of information from all over, some here, some there, there does not seem to be a definitive overall guide of how to actually achieve what should be a relatively simple task, so I thought I&#8217;d write one.

Firstly let me start by detailing my hardware so it can be reproduced.

I use an Ubuntu system with these specs.:-

[SIZE=1]]System: Host: linuxmint Kernel: 5.0.12-050012-generic x86_64 bits: 64 Desktop: KDE Plasma 5.12.7 
Distro: Ubuntu 18.04.2 LTS 
Machine device: desktop Mobo: ASUSTeK model: STRIX Z270E GAMING v: Rev 1.xx serial: 170706774500147
UEFI: American Megatrends v: 1302 date: 03/15/2018
CPU: Quad core Intel Core i7-7700K (-MT-MCP-) cache: 8192 KB
clock speeds: max: 4500 MHz 1: 4500 MHz 2: 4500 MHz 3: 4499 MHz 4: 4500 MHz 5: 4500 MHz 6: 4500 MHz 7: 4500 MHz 8: 4499 MHz
Graphics: Card: NVIDIA GM206 [GeForce GTX 960]
Display Server: x11 (X.Org 1.19.6 ) driver: nvidia Resolution: 1920x1080@50.04hz 
OpenGL: renderer: GeForce GTX 960/PCIe/SSE2 version: 4.6.0 NVIDIA 390.116
Audio: Card NVIDIA Device 0fba driver: snd_hda_intel Sound: ALSA v: k5.0.12-050012-generic 
Network: Card: Intel Ethernet Connection (2) I219-V driver: e1000e 
IF: eth0 state: up speed: 1000 Mbps duplex: full mac: 10:7b:44***
Drives:HDD Total Size: 9283.8GB (81.2% used) 
ID-1: /dev/sda model: Samsung_SSD_840 size: 250.1GB 
ID-2: /dev/sdb model: ST4000LM024 size: 4000.8GB
ID-3: /dev/sdc model: TOSHIBA_MD04ACA5 size: 5001.0GB
ID-4: USB /dev/sdd model: Mass size: 32.0GB 
Partition: ID-1: / size: 59G used: 24G (41%) fs: btrfs dev: /dev/sda5 
ID-2: /home size: 75G used: 23G (32%) fs: btrfs dev: /dev/sda6 
RAID: No RAID devices: /proc/mdstat, md_mod kernel module present 
Sensors: System Temperatures: cpu: 55.0C mobo: N/A gpu: 33C 
Fan Speeds (in rpm): cpu: 0 
Info: Processes: 367 Uptime: 58 min Memory: 3000.4/15970.6MB Client: Shell (bash) inxi: 2.3.56 [/SIZE]

My USB drive is a Samsung EVO class 10 orange 32gb microSD plugged into a USB adaptor on a USB-3 port, taken from a dashcam so is designed for multiple writes, it certainly has had a few while doing this exercise.

Let's get started-

Partition it with gparted to a gpt system and format to one contiguous Fat32 partition.  Then change the flags to esp/boot/legacy_boot

Then mount it to /mnt/&#8221;whatever&#8221;, I chose /mnt/pen.

mkdir pen
mount /dev/sdd1 /mnt/pen

cd /mnt/pen

mkdir /mnt/pen/iso

After much research this is the golden command required:-

 [COLOR=#ff0000]**grub-install --target x86_64-efi --efi-directory /mnt/pen --boot-directory=/mnt/pen &#8211;removable**[/COLOR]

This will create the bootable UEFI pen drive, now all that is required is to populate the /mnt/pen/iso with your favourite distributions and create and write/modify the grub.cfg file for the menus.
This is my command list for the install:-

root@linuxmint:/home/tony# mkdir /mnt/pen
root@linuxmint:/home/tony# mount /dev/sdd1 /mnt/pen 
root@linuxmint:/home/tony# cd /mnt/pen 
root@linuxmint:/mnt/pen# grub-install --target x86_64-efi --efi-directory /mnt/pen --boot-directory=/mnt/pen --removable 
Installing for x86_64-efi platform. 
Installation finished. No error reported. 
root@linuxmint:/mnt/pen#

 Here is a sample grub menu file: /mnt/pen/EFI/BOOT/grub.cfg

[I]search.fs_uuid 3D9C-0693 root hd3,gpt1 
set prefix=($root)'/grub'
configfile $prefix/grub.cfg

submenu "Lubuntu 19.04" {

    submenu "Lubuntu 19.04" {

	menuentry 'Lubuntu 19.04 amd64' {
		set isofile="/iso/lubuntu.iso"
		loopback loop $isofile
		linux (loop)/casper/vmlinuz boot=casper iso-scan/filename=$isofile liveimg noprompt noeject --
		initrd (loop)/casper/initrd.lz
	}
}

	menuentry 'Lubuntu 19.04 amd64 (failsafe)' {
		set isofile="/iso/lubuntu.iso"
		loopback loop $isofile
		linux (loop)/casper/vmlinuz boot=casper iso-scan/filename=$isofile liveimg noeject nomodeset --
		initrd (loop)/casper/initrd.lz
	}
}
#edited the Lubuntu entry, cut and pasted the 32-bit instead of the amd64, now corrected-thanks to OldFred!


submenu "Linux Mint 19" {
    menuentry 'Mint 18 amd64' {
        set isofile="/iso/linuxmint-19.1-cinnamon-64bit.iso"
        loopback loop $isofile
        linux (loop)/casper/vmlinuz boot=casper iso-scan/filename=$isofile liveimg noprompt noeject --
        initrd (loop)/casper/initrd.lz
    }
    menuentry 'Mint 19 amd64 (failsafe)' {
        set isofile="/iso/linuxmint-19.1-cinnamon-64bit.iso"
        loopback loop $isofile
        set gfxpayload=800x600x16,800x600
        linux (loop)/casper/vmlinuz boot=casper iso-scan/filename=$isofile liveimg noeject nomodeset noapic --
        initrd (loop)/casper/initrd.lz
    }
}[/I]

The first part of the file is critical, it has to point to the actual physical location of the pen drive.

In my case this was:-  search.fs_uuid 3D9C-0693 root hd3,gpt1

**Yours will probably be different!**  Check with the command: blkid     
This will give you the UUID of your pendrive and it&#8217;s hierarchical location in your system.
The explanation of mine is:-

[I]/dev/sda1: LABEL="SYSTEM" UUID="32B3-4D0D" TYPE="vfat" PARTLABEL="EFI system partition" PARTUUID="9f6b7f95-7a39-42ec-b
033-6896e47b8aee" [/I][COLOR=#00ff00]This is my system&#8217;s boot partition, the location as the UEFI system recognises it is HD0,1
[/COLOR][I]
/dev/sda3: LABEL="Windows" UUID="DA36B3C936B3A543" TYPE="ntfs" PARTLABEL="Basic data partition" PARTUUID="aa7da52a-a5f
9-4974-b00f-1279414b021d" [/I][COLOR=#00ff00]This is my system&#8217;s Windows partition, the location as the UEFI system recognises it is HD0,3
 [/COLOR][I]
/dev/sda4: UUID="DEB20F28B20F04AD" TYPE="ntfs" PARTUUID="a90b1de9-43d8-4672-8498-143e40548463" [/I][COLOR=#00ff00]This is my system&#8217;s legacy Window&#8217;s system partition, unused now, the location as the UEFI system recognises it is HD0,4 [/COLOR][I]

/dev/sda5: UUID="6c0ab85c-3f8b-4b7c-8ef1-b0ed9ae4d8ad" UUID_SUB="ca739b39-326d-4a0f-85fb-1bc248c1939d" TYPE="btrfs" PA
RTUUID="3afb5ed4-63b3-46a0-8d18-efc92402cc5a" [/I][COLOR=#00ff00]This is my system&#8217;s kubuntu root / partition, the location as the UEFI system recognises it is HD0,5 
[/COLOR][I]
/dev/sda6: UUID="c68f50bd-e237-4b5b-b12e-ba909f3b1138" UUID_SUB="819004c9-54df-4e72-a7aa-2653e54063c1" TYPE="btrfs" PA
RTUUID="cca08698-e920-486e-9695-a4e81fc48de4" [/I][COLOR=#00ff00]This is my system&#8217;s kubuntu /home partition, the location as the UEFI system recognises it is HD0,6 
[/COLOR][I]
/dev/sda7: LABEL="Windows RE tools" UUID="B8C2B429C2B3EA30" TYPE="ntfs" PARTLABEL="Basic data partition" PARTUUID="0c7
14045-2095-456a-a9f1-f1c4723d8a9d" [/I][COLOR=#00ff00]This is my system&#8217;s Windows tools partition, the location as the UEFI system recognises it is HD0,7
[/COLOR][I]
/dev/sdc1: LABEL="tv" UUID="6E66CE4866CE112F" TYPE="ntfs" PARTLABEL="Basic data partition" PARTUUID="d9118715-a532-4b4
f-8ba0-01fe09c65398" [/I][COLOR=#00ff00]This is my system&#8217;s multemedia storage partition, the location as the UEFI system recognises it is HD2,1[/COLOR][I] 

/dev/sdb1: LABEL="data" UUID="F2E89BB2E89B7397" TYPE="ntfs" PARTLABEL="Basic data partition" PARTUUID="1ce6123a-1742-4
ca4-9b71-c495bca489af" [/I][COLOR=#00ff00]This is my system&#8217;s main data storage partition, the location as the UEFI system recognises it is HD1,1
[/COLOR][I]
[COLOR=#b22222]/dev/sdd1: UUID="3D9C-0693" TYPE="vfat" PARTUUID="ad1fdc32-fbcb-4d36-977d-ddb60e62dd1d"[/COLOR] [/I][COLOR=#00ff00]This is my system&#8217;s USB pendrive storage partition, the location as the UEFI system recognises it is HD3,1[/COLOR][I]

/dev/sda2: PARTLABEL="Microsoft reserved partition" PARTUUID="29e072d8-988e-41e5-ae9e-255f8050fa4f"
[/I][COLOR=#00ff00]This is my system&#8217;s Windows recovery partition, the location as the UEFI system recognises it is HD0,2[/COLOR]


I hope this will help those of you who like me have searched in vain for a less painful way of creating a multiboot UEFI pendrive.
Please feel free to correct any errors or omissions in my how-to-I am not a guru!:)  I struggle along with everyone else.
Cheers, Tony.

---

### Post by oldfred on 2019-07-12
Do not know Lubuntu configurations, but most Ubuntu 32 bit versions need  BOOTIA32.EFI added to boot in 32 bit UEFI mode. And that is only for a very few systems with 32 bit UEFI, but 64 bit CPU.

Standard UEFI boot is 64 bit using \EFI\BOOT\BOOTx64.EFI.     

For my smaller flash drives, I have always done exactly what you  have done. But I now have multiple larger flash drives, and put a full Ubuntu UEFI install in a 16 or 20GB / partition, 100MB ESP,  and add ISO into another partition and/or use rest of flash drive for data backup/storage.

Boot drive in BIOS/UEFI/grub is always hd0, but search by UUID or label should always work. 
I did have one system with many drives where it seemed to stop search after multiple drives & then some empty drive spaces & never found sdg even by UUID. And on reboot sdg became hd0.

I always found getting path (since before boot) & boot parameters correct as major issues. Parameters for boot stanza are always in ISO, so sometimes I have to open ISO and see what it's grub uses. For example they changed vmlinuz to vmlinuz.efi and recently back to vmlinuz.

       [https://help.ubuntu.com/community/Grub2/ISOBoot](https://help.ubuntu.com/community/Grub2/ISOBoot)
examples
[https://gist.github.com/Pysis868/27203177bdef15fbb70c](https://gist.github.com/Pysis868/27203177bdef15fbb70c) 
    
If you want grub2 to install boot loader to any ESP other than sda or first NVMe drive (Ubiquity default regardless of settings in Ubiquity), see this:
       Posted work around to manually unmount & mount correct ESP during install
[https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/1396379](https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/1396379)

For most installs now, I use an ISO partition on sda (SSD) to install to sdb or flash drive, or an ISO partition on sdb to install to sda. I always now use toram parameter so ISO is in RAM for install.

---

### Post by vidtek on 2019-07-12
Thanks OldFred I cut and pasted the wrong entry for Lubuntu, now corrected.  Thanks for pointing this out.
Tony.

---

