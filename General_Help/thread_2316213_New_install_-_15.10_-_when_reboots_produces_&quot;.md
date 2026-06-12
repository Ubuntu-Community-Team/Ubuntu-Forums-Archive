---
title: "New install - 15.10 - when reboots produces &quot;device not found error"
date: 2016-03-06
forum: General Help
---

### Post by Fsirett on 2016-03-06
I am sorry to have to bother this forum again, but I have another rather irritating problem.

First of all, I have a recently rebuilt machine. I changed nearly everything but the drives, at least most of them, and this problem only came about in the last week or so. 

When I foot up I am getting an error:

"No such device: ee0a04a6-591c-4e9a-8b85-d7c7b1ab10d8"

And then goes to grub rescue.

Blkid gives me this:```
ubuntu@ubuntu:~$ blkid
/dev/sda1: UUID="80818117-a220-43cc-a2d8-49492e04194a" TYPE="ext4" PARTUUID="0007e476-01"
/dev/sda3: LABEL="One" UUID="bd7d5230-2c78-4b34-9ae2-21d28f05e431" TYPE="ext4" PARTUUID="0007e476-03"
/dev/sda6: UUID="355f357b-0e22-4453-8fc5-bb78303f7df8" TYPE="ext4" PARTUUID="0007e476-06"
/dev/sdb1: UUID="bc2d4482-c278-40e8-9862-cdd7e4679ce6" TYPE="ext4" PARTUUID="0008b2e1-01"
/dev/sdc1: LABEL="6a" UUID="da5ddedd-0748-49a5-8483-db9137e48e85" SEC_TYPE="ext2" TYPE="ext3" PARTUUID="5d1c6b14-01"
/dev/sdc2: LABEL="6b Documents" UUID="d8658713-6c7a-4e06-84c3-4046c6b62393" SEC_TYPE="ext2" TYPE="ext3" PARTUUID="5d1c6b14-02"
/dev/sdc3: LABEL="6c Music" UUID="1f61b3ec-0a12-4b4a-ad3e-db550d98a244" SEC_TYPE="ext2" TYPE="ext3" PARTUUID="5d1c6b14-03"
/dev/sdc4: LABEL="6d Downloads" UUID="3fde030a-4b08-4c33-9025-6e81bf0d06c7" SEC_TYPE="ext2" TYPE="ext3" PARTUUID="5d1c6b14-04"
/dev/sdd1: LABEL="Five" UUID="b896603d-f8e3-4e1e-9434-51b8f1dedcd0" TYPE="ext4" PARTUUID="0006e6a2-01"
/dev/sdd2: LABEL="Four" UUID="64e5b3bb-9838-4187-9fff-2afc6e7f2c92" TYPE="ext4" PARTUUID="0006e6a2-02"
/dev/sde1: LABEL="My Passport" UUID="B4D48115D480DB4E" TYPE="ntfs" PARTUUID="0004a183-01"
/dev/sdf1: LABEL="MYLINUXLIVE" UUID="A017-5C68" TYPE="vfat" PARTUUID="0004c543-01"

```

My boot repair report is:

[URL="http://paste.ubuntu.com/15305364/"]http://paste.ubuntu.com/15305364/

[/URL]I can seeit is line 24 and 33 of this report where the request is being made, but I have no idea how to delete this request

I scanned the disk for errors from a live USB and it all cme out clear.

Now the history. First I have the /home on another partition on another drive. I like the idea of easy upgrades. The system ran (more or less) fine until a week or ten days ago when it began throwing up errors on booting. I reinstalled and the problem just got worse. I read that I might be better off installing for my new UEFI system and so I completely redid my partitions for the system and installed again yesterday. Initial boot went fine and the computer was a real charmer after that, but this morning when I booted up it gave me this error...AGAIN!

My methods of dealing with this have been to run the Boot-Repair and that has been solving the problem for the next boot up but then the entire thing just collapses again when I next reboot. This will be the third reinstall this week and yet the problem persists.

I really should know more, but I do not. Looking over past records and problems I am now wondering if the device with this UUID ever existed at all! 

I do not know if it matters at all, but the installs were all done with the same USB and the same version of Ubuntu (15.10) on that. In fact it is the same one I am running as we speak.

Cheers for your help

Frank Sirett

---

### Post by howefield on 2016-03-06
Sounds like fstab is looking for a UUID which one of disks/partitions had before you messed around with them but is now changed.

Check the UUIDs in /etc/fstab vs what you have above.

---

### Post by Fsirett on 2016-03-06
Cheers, I am afraid, after a quick search on how to get a little information on getting the fstab report I am no more enlightened than before, What commands do I use? I promise I will keep the information safe and, hopefully, never have to ask again!

---

### Post by howefield on 2016-03-06
Using the terminal command..

```
cat /etc/fstab
```

should output the contents of the fstab file.

Let us know how you get on and if you need help, whether you want the terminal or GUI method ?

---

### Post by Fsirett on 2016-03-06
Cheers! I tried that one and I think the results might be disappointing. 

Here is what I got:
```
ubuntu@ubuntu:~$ cat /etc/fstab
overlay / overlay rw 0 0
tmpfs /tmp tmpfs nosuid,nodev 0 0
/dev/sda5 swap swap defaults 0 0
/dev/sdb5 swap swap defaults 0 0

```

I see there is a gksu command I just found, but being on a live usb, i am now getting everything together to run gksu. My internet is very slow today,

As I returned to the system, it threw up a warning that my / file was running out of space! this seems odd since it was a new install late yesterday! It seems to say it is filling a download folder other than in my /home folder that is located with bags of room. Is this possibly part of the problem?

Now it is getting ridiculous. I trashed the downloads but it is still refusing to update my repositories and so I cannot get at the gksu command. Something is very wrong here.

---

### Post by howefield on 2016-03-06
That is the fstab from the Live media, not your installed system.

I'm confused with your last edit, are you back into your system ?

PS. You can use sudo -H rather than gksudo.

---

### Post by Fsirett on 2016-03-06
Cheers! The -H command will be coming in very handy in future. I was just thinking that I might have been very stupid in thinking the problem came from my system while I was on Live media.

Can I get the fstab for my system from a live USB? I am afraid I think I once ran into that possibility but I do not remember the commands, Sorry.

Another stupid question. Can I run the etc/fstab check from the Grub recovery terminal when I try to reboot into the system, assuming it presents the same screen?

---

### Post by howefield on 2016-03-06
> **Fsirett said:**
> Can I get the fstab for my system from a live USB? I am afraid I think I once ran into that possibility but I do not remember the commands, Sorry.

Might be easier for you to fire up the File Manager and navigate to the disk/partition where / is located and from there.. /etc/fstab

---

### Post by Fsirett on 2016-03-06
Sorry for the delay, it took me a while to find the file. I am really stupid today!

in any case, I do believe this is the etc/fstab file:

```
# /etc/fstab: static file system information.
#
# Use 'blkid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
# / was on /dev/sda1 during installation
UUID=80818117-a220-43cc-a2d8-49492e04194a /               ext4    errors=remount-ro 0       1
# /home was on /dev/sda6 during installation
UUID="da5ddedd-0748-49a5-8483-db9137e48e85" /home           ext3     defaults        0       2
# swap was on /dev/sda5 during installation
UUID=006df67e-4703-4ad0-90ef-f8ff2cca88fc none            swap    sw              0       0
# swap was on /dev/sdb5 during installation
UUID=2c9bc47c-925d-4123-b518-93580a5a1eba none            swap    sw              0       0
UUID=4433-2211    /boot/efi    vfat    defaults    0    1
```

I do hope that is the right file!

---

### Post by Fsirett on 2016-03-06
Just thinking out loud and probably wasting time, but since the system boots up fine after I have run the boot repair disk and the next boot this problem appears, it must be added to the system after the first boot or it is failing to see the right location on the second boot and defaulting to an ancient drive, although that does seem odd, considering this is a completely new install.

I am then thinking that this is a new motherboard (and processor) and they are the first I have had with UEFI. the system is installed as a UEFI system, as suggested, and that may be the reason as well. 

I am now wondering why this was not persistent earlier when I first installed the same system from the same USB. 

Curiouser and curiouser

---

### Post by Fsirett on 2016-03-06
I have been looking around the net for answers, and I found this:

[https://bbs.archlinux.org/viewtopic.php?id=163536](https://bbs.archlinux.org/viewtopic.php?id=163536)

What seems to make some sense to me is where they say the problem can be solves with the command:```
grub-mkconfig -o /boot/grub/grub.cfg
```
  
Then rebooting.

As far as I can understand, and my brain is not good today, this seems to have worked, but they are using this with Arch Linux. Is this of any value to me? Can I alter it in some way to help? Not finding the culprit UUID is bothering me and has mme wondering what I can do.

Cheers

---

### Post by Fsirett on 2016-03-06
I am casting about for ideas to solve this problem and, if nobody tells me this is a wasted effort, I am going to remove a hard drive or two in the morning to see if the phantom UUID disappears with it. I know that does not seem to make sense in any logical way as the unit does not seem to exist in any case, but I am now more than desperate. Any help? other ideas?

Cheers

---

### Post by oldfred on 2016-03-06
Your fstab in sda1 was in the Summary Report from Boot-Repair.

But it shows the /boot/efi being mounted which is from an UEFI install. But that does not exist, so would show errors.
But that is not UUID you are showing in first post.

But all your drives are MBR (msdos) and UEFI normally uses gpt.
And you show grub in the MBR of sda (and sdb and sdd) for BIOS boot.
So Which way are you booting, and that is controlled by UEFI/BIOS. 

What brand/model system or motherboard. And what video?

Do not run autofix with Boot-Repair as that installs one grub to all MBR. Use advanced mode only.
And it gives a message on trying to install in UEFI mode but no ESP - efi system partition.

---

### Post by Fsirett on 2016-03-06
What a fine time I am having with this! Third try at a reply and no success yet. My fault, I fear.

In any case, thank you very much for your response. I now see a glimmer of reason to this problem. So encouraging!

First my motherboard is a Gigabyte GA-F2A88XM-D3H and the processor is an AMD A 10-7XXX series. I know it is not a 7800 but it is one below that. 

The graphics are the chip and board standards, I do not need much in the way of graphics, not much of a game player.

I used the guidance from [http://ivanblagojevic.com/how-to-install-ubuntu-14-04-lts-on-an-empty-hard-disk-tutorial/](http://ivanblagojevic.com/how-to-install-ubuntu-14-04-lts-on-an-empty-hard-disk-tutorial/) to help me do the last installation. i wanted to make fewer errors- forlorn hope!

Because I had read about problems with UEFI and this being my first UEFI board, I used every UEFI option in this install. Just to be safe(!?)

My /home folder is on another disk, so reinstalling the system is not a problem, but if you have any advice on how to do it properly in future you will have earned my eternal gratitude!

Some days are better than others, but today has been impossible for me to think past the front door, this has all probably been put before me earlier but I was unable to grasp the significance

Cheers

---

### Post by Fsirett on 2016-03-06
You asked about my video system. I had to look up the commands to get me to see them, I assume that this is what you want:

```
ubuntu@ubuntu:~$ lspci -v
00:00.0 Host bridge: Advanced Micro Devices, Inc. [AMD] Family 15h (Models 30h-3fh) Processor Root Complex
    Subsystem: Advanced Micro Devices, Inc. [AMD] Family 15h (Models 30h-3fh) Processor Root Complex
    Flags: bus master, fast devsel, latency 0

00:00.2 IOMMU: Advanced Micro Devices, Inc. [AMD] Family 15h (Models 30h-3fh) I/O Memory Management Unit
    Subsystem: Advanced Micro Devices, Inc. [AMD] Family 15h (Models 30h-3fh) I/O Memory Management Unit
    Flags: fast devsel, IRQ 24
    Capabilities: <access denied>

00:01.0 VGA compatible controller: Advanced Micro Devices, Inc. [AMD/ATI] Kaveri [Radeon R7 Graphics] (prog-if 00 [VGA controller])
    Subsystem: Gigabyte Technology Co., Ltd Device d000
    Flags: bus master, fast devsel, latency 0, IRQ 47
    Memory at c0000000 (64-bit, prefetchable) [size=256M]
    Memory at d0000000 (64-bit, prefetchable) [size=8M]
    I/O ports at f000 [size=256]
    Memory at feb00000 (32-bit, non-prefetchable) [size=256K]
    Expansion ROM at feb40000 [disabled] [size=128K]
    Capabilities: <access denied>
    Kernel driver in use: radeon

00:01.1 Audio device: Advanced Micro Devices, Inc. [AMD/ATI] Kaveri HDMI/DP Audio Controller
    Subsystem: Gigabyte Technology Co., Ltd Device a002
    Flags: bus master, fast devsel, latency 0, IRQ 49
    Memory at feb64000 (64-bit, non-prefetchable) [size=16K]
    Capabilities: <access denied>
    Kernel driver in use: snd_hda_intel

00:02.0 Host bridge: Advanced Micro Devices, Inc. [AMD] Device 1424
    Flags: fast devsel

00:03.0 Host bridge: Advanced Micro Devices, Inc. [AMD] Device 1424
    Flags: fast devsel

00:03.1 PCI bridge: Advanced Micro Devices, Inc. [AMD] Family 15h (Models 30h-3fh) Processor Root Port (prog-if 00 [Normal decode])
    Flags: bus master, fast devsel, latency 0, IRQ 25
    Bus: primary=00, secondary=01, subordinate=01, sec-latency=0
    I/O behind bridge: 0000e000-0000efff
    Memory behind bridge: fea00000-feafffff
    Prefetchable memory behind bridge: 00000000d0800000-00000000d08fffff
    Capabilities: <access denied>
    Kernel driver in use: pcieport

00:04.0 Host bridge: Advanced Micro Devices, Inc. [AMD] Device 1424
    Flags: fast devsel

00:10.0 USB controller: Advanced Micro Devices, Inc. [AMD] FCH USB XHCI Controller (rev 09) (prog-if 30 [XHCI])
    Subsystem: Gigabyte Technology Co., Ltd Device 5004
    Flags: bus master, fast devsel, latency 0, IRQ 18
    Memory at feb6a000 (64-bit, non-prefetchable) [size=8K]
    Capabilities: <access denied>
    Kernel driver in use: xhci_hcd

00:10.1 USB controller: Advanced Micro Devices, Inc. [AMD] FCH USB XHCI Controller (rev 09) (prog-if 30 [XHCI])
    Subsystem: Gigabyte Technology Co., Ltd Device 5004
    Flags: bus master, fast devsel, latency 0, IRQ 17
    Memory at feb68000 (64-bit, non-prefetchable) [size=8K]
    Capabilities: <access denied>
    Kernel driver in use: xhci_hcd

00:11.0 SATA controller: Advanced Micro Devices, Inc. [AMD] FCH SATA Controller [AHCI mode] (rev 40) (prog-if 01 [AHCI 1.0])
    Subsystem: Gigabyte Technology Co., Ltd Device b002
    Flags: bus master, 66MHz, medium devsel, latency 32, IRQ 37
    I/O ports at f140 [size=8]
    I/O ports at f130 [size=4]
    I/O ports at f120 [size=8]
    I/O ports at f110 [size=4]
    I/O ports at f100 [size=16]
    Memory at feb71000 (32-bit, non-prefetchable) [size=2K]
    Capabilities: <access denied>
    Kernel driver in use: ahci

00:12.0 USB controller: Advanced Micro Devices, Inc. [AMD] FCH USB OHCI Controller (rev 11) (prog-if 10 [OHCI])
    Subsystem: Gigabyte Technology Co., Ltd Device 5004
    Flags: bus master, 66MHz, medium devsel, latency 32, IRQ 18
    Memory at feb70000 (32-bit, non-prefetchable) [size=4K]
    Kernel driver in use: ohci-pci

00:12.2 USB controller: Advanced Micro Devices, Inc. [AMD] FCH USB EHCI Controller (rev 11) (prog-if 20 [EHCI])
    Subsystem: Gigabyte Technology Co., Ltd Device 5004
    Flags: bus master, 66MHz, medium devsel, latency 32, IRQ 17
    Memory at feb6f000 (32-bit, non-prefetchable) [size=256]
    Capabilities: <access denied>
    Kernel driver in use: ehci-pci

00:13.0 USB controller: Advanced Micro Devices, Inc. [AMD] FCH USB OHCI Controller (rev 11) (prog-if 10 [OHCI])
    Subsystem: Gigabyte Technology Co., Ltd Device 5004
    Flags: bus master, 66MHz, medium devsel, latency 32, IRQ 18
    Memory at feb6e000 (32-bit, non-prefetchable) [size=4K]
    Kernel driver in use: ohci-pci

00:13.2 USB controller: Advanced Micro Devices, Inc. [AMD] FCH USB EHCI Controller (rev 11) (prog-if 20 [EHCI])
    Subsystem: Gigabyte Technology Co., Ltd Device 5004
    Flags: bus master, 66MHz, medium devsel, latency 32, IRQ 17
    Memory at feb6d000 (32-bit, non-prefetchable) [size=256]
    Capabilities: <access denied>
    Kernel driver in use: ehci-pci

00:14.0 SMBus: Advanced Micro Devices, Inc. [AMD] FCH SMBus Controller (rev 16)
    Subsystem: Advanced Micro Devices, Inc. [AMD] FCH SMBus Controller
    Flags: 66MHz, medium devsel
    Kernel driver in use: piix4_smbus

00:14.2 Audio device: Advanced Micro Devices, Inc. [AMD] FCH Azalia Controller (rev 01)
    Subsystem: Gigabyte Technology Co., Ltd Device a002
    Flags: bus master, slow devsel, latency 32, IRQ 16
    Memory at feb60000 (64-bit, non-prefetchable) [size=16K]
    Capabilities: <access denied>
    Kernel driver in use: snd_hda_intel

00:14.3 ISA bridge: Advanced Micro Devices, Inc. [AMD] FCH LPC Bridge (rev 11)
    Subsystem: Advanced Micro Devices, Inc. [AMD] FCH LPC Bridge
    Flags: bus master, 66MHz, medium devsel, latency 0

00:14.4 PCI bridge: Advanced Micro Devices, Inc. [AMD] FCH PCI Bridge (rev 40) (prog-if 01 [Subtractive decode])
    Flags: bus master, VGA palette snoop, 66MHz, medium devsel, latency 64
    Bus: primary=00, secondary=02, subordinate=02, sec-latency=64

00:14.5 USB controller: Advanced Micro Devices, Inc. [AMD] FCH USB OHCI Controller (rev 11) (prog-if 10 [OHCI])
    Subsystem: Gigabyte Technology Co., Ltd Device 5004
    Flags: bus master, 66MHz, medium devsel, latency 32, IRQ 18
    Memory at feb6c000 (32-bit, non-prefetchable) [size=4K]
    Kernel driver in use: ohci-pci

00:18.0 Host bridge: Advanced Micro Devices, Inc. [AMD] Family 15h (Models 30h-3fh) Processor Function 0
    Flags: fast devsel

00:18.1 Host bridge: Advanced Micro Devices, Inc. [AMD] Family 15h (Models 30h-3fh) Processor Function 1
    Flags: fast devsel

00:18.2 Host bridge: Advanced Micro Devices, Inc. [AMD] Family 15h (Models 30h-3fh) Processor Function 2
    Flags: fast devsel

00:18.3 Host bridge: Advanced Micro Devices, Inc. [AMD] Family 15h (Models 30h-3fh) Processor Function 3
    Flags: fast devsel
    Capabilities: <access denied>
    Kernel driver in use: k10temp

00:18.4 Host bridge: Advanced Micro Devices, Inc. [AMD] Family 15h (Models 30h-3fh) Processor Function 4
    Flags: fast devsel
    Kernel driver in use: fam15h_power

00:18.5 Host bridge: Advanced Micro Devices, Inc. [AMD] Family 15h (Models 30h-3fh) Processor Function 5
    Flags: fast devsel

01:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller (rev 0c)
    Subsystem: Gigabyte Technology Co., Ltd Motherboard
    Flags: bus master, fast devsel, latency 0, IRQ 45
    I/O ports at e000 [size=256]
    Memory at fea00000 (64-bit, non-prefetchable) [size=4K]
    Memory at d0800000 (64-bit, prefetchable) [size=16K]
    Capabilities: <access denied>
    Kernel driver in use: r8169

ubuntu@ubuntu:~$ 

```

I assume that is everything you need. Probably too much, I was in a hurry and I put in the first command that looked as if it would do the trick

Cheers

---

### Post by oldfred on 2016-03-06
Your link is for a BIOS install which can use the 35 year old MBR(msdos) partitioning or the newer gpt(GUID) partitioning.
Windows only boots from MBR with BIOS.
Windows only boots from gpt with UEFI.
But Ubuntu can boot from gpt with either UEFI if you have ESP - efi system partition or from BIOS if you have bios_grub partition.

Your drives all are currently MBR. While you can convert a drive, I have never done it. But I knew years ago I would eventually convert to UEFI, so all new or totally reformatted drives since about 2011 have been gpt. Most of my large flash drives now are gpt also.

From an install you can read data in gpt or MBR. It was only XP that could not read gpt. My old XP install was on MBR, Ubuntu on a gpt drive and I still had most data on a MBR drive.

So first decide if you want UEFI or BIOS and then partition boot drive to match.

I do not know AMD as I have nVidia and Intel video systems. If you do not have boot issues then the driver must be ok.

If you want to reinstall with UEFI, best to review link below in my signature. It is a lot and has more links to other useful info. But UEFI is more complex as it is both new UEFI with more features and the old BIOS. How you boot install media, UEFI or BIOS is how it installs.

If you just want system to work with BIOS & MBR, you should just need grub in MBR and perhaps some other fixes, like removing efi entry in fstab.

---

### Post by Fsirett on 2016-03-06
Cheers for that! I have been looking at your link and I am not completely certain how I can change. I have one new drive, but I am in need of others and so will change to complete UEFI when i add drives, thereby moving information to the new drive and then converting them all to UEFI with fewer complications. MBR is fine for me right at the moment. 

I am now checking to see if I understand how to convert the whole thing to strictly MBR, but in the meantime, would I be okay if I just reinstalled without any UEFI options? I know the bios has options for UEfI only, legacy, or UEFi and Legacy. Right now it is the latter option, but since I am having this problem, I have probably got a mix and match situation going on. 

I am looking again at your UEFI thread, but I cannot guarantee that I will fathom it all.

Cheers

P.S I have just noticed this paragraph in your post:

"Boot-Repair will convert a BIOS install to UEFI by uninstalling grub-pc, and installing grub-efi, if gpt partitioned.
     It can update system to secure boot if you boot in secure boot mode. But then the grub entry for Windows may not work."

Would I be correct in assuming that is exactly the problem I am having?

---

### Post by Fsirett on 2016-03-06
I am now using boot repair in the advanced pages to reinstall the grub. It has said something about UEFi but I have ignored it in the hopes I can make all this work. Should a disaster happen I leave thi s log to guide followers down this treacherous path.

---

### Post by goofprog on 2016-03-06
At least your brain is functioning.  I only know that there is a grub v1.x and a grub v2.x so maybe the command varies on the version of grub being used.

---

### Post by Fsirett on 2016-03-06
I am not certain I know about the versions of the Grub, However, I do know that now that I went ahead with Boot repair - advanced, I replaced the Grub and the machine rebooted! It warned me about having UEFI on board, but I am going to wait until I replace disks, back up everything to the newer disks and reinstall a complete UEFI when it can do less damage to me and my poor head! 

This has been an all day fight, but I just take solace in the fact that when I was using Windows (XP pro) something like this would take two or three days to solve and then another day to reinstall everything. I know this because it was just about a biannual occasion. 

My undying thanks to The two chaps who so generously helped me along here. I shall remember their tips and tricks and all the help they so generously gave. I will not be thanking my family, my wife or anyone else at the moment...I never liked award shows and gratitude in the real world is moving inexorably that way. I shall not share that fashion.

I think we can mark this case closed!

Cheers all! I should come here more often, Fascinating problems for me to comisserate or puzzle over. One day I might even be able to even offer a word of advice! Will wonders never cease?

Cheers again

Frank Sirett

---

### Post by goofprog on 2016-03-06
I did nothing and thank you for the Cheers.  I needed that today because I feel like Eeyore.  (it is a famous Disney character)

---

### Post by oldfred on 2016-03-06
Glad you got it working. :)

Is is not UEFI or BIOS on your data drives, but type of partitioning gpt or MBR. Only boot drive should be gpt for UEFI boot. 
But live installer is both UEFI & BIOS on FAT32 partitioned drive that may be MBR or gpt.

I used gpt with BIOS boot since about Ubuntu 10.10 and had some gpt drives and some MBR. But over time converted most to gpt.
And with new system only used gpt and installed in UEFI boot mode.

---

