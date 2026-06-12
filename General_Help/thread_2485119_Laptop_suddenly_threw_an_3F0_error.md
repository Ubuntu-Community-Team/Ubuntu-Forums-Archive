---
title: "Laptop suddenly threw an 3F0 error"
date: 2023-03-20
forum: General Help
---

### Post by sld-dls on 2023-03-20
Good evening!

My laptop all of a sudden stopped booting and began to throw a 3F0 error (Please install operation system on your hard drive)

I was suggested to use a boot-repair tool, but all it did was to generate this report: [https://paste.ubuntu.com/p/pmg9nB6pFc/](https://paste.ubuntu.com/p/pmg9nB6pFc/)

I don't know what to do, please, help

---

### Post by ajgreeny on 2023-03-20
Well, it seems that the boot-info report is suggesting that there is no hard disk detected in your system and only the 4GB flash drive is seen
```
fdisk -l (filtered): ___________________________________________________________

Disk sda: 3.92 GiB, 4203741184 bytes, 8210432 sectors
Disk identifier: A09DB2B8-B5F6-43AE-AFB3-91E0A90189A1
        Start     End Sectors  Size Type
sda1       64 7129427 7129364  3.4G Microsoft basic data
sda2  7129428 7137923    8496  4.1M EFI System
sda3  7137924 7138523     600  300K Microsoft basic data
sda4  7139328 8210368 1071041  523M Linux filesystem

parted -lm (filtered): _________________________________________________________

sda:4204MB:scsi:512:512:gpt:Generic Flash Disk:;
1:32.8kB:3650MB:3650MB::ISO9660:hidden, msftdata;
2:3650MB:3655MB:4350kB::Appended2:boot, esp;
3:3655MB:3655MB:307kB::Gap1:hidden, msftdata;
4:3655MB:4204MB:548MB:ext4::;

```
Restart your machine and go to the BIOS/UEFI firmware which you normally get to from a keypress shown on screen just after powering on, eg **Press F2 for system setup** or similar words, and once in there search for information about the hardware and disks detected.

---

### Post by sld-dls on 2023-03-21
The thing is that it randomly detected the ssd an hour later.
I reinstalled grub, it worked fine for a while.
Then it suddenly stopped to see the drive again.

---

### Post by ActionParsnip on 2023-03-21
Why EFI for Ubuntu only?

---

### Post by TheFu on 2023-03-21
If the storage is installed, check the connections - replace SATA cables.  Try a different SATA port.  For m.2 connections, try a different m.2 on the motherboard. Check for overheating. See of there are firmware updates specific to your model of m.2 SSD and install those.  Be certain to have excellent backups.

Background story ... not laptop, but desktop storage disappearing.

Yesterday one of my 4TB HDDs in an external enclosure "disappeared".  I don't know exactly when it disappeared, just sometime overnight.  The initial error was that a few of the file systems where missing superblocks.  

So I started working backwards.  
Where's the file system?  it isn't showing up. Gone.
Which partition? sda3
Which disk?  One of the 4TB Hitachis (I have a few in the system)

Where's the disk? ... that's a little harder.  Basically, I had to go through backup data where I capture storage information nightly.  I dump this storage information into text files and include those text files in my backup data.  I was able to determine the exact drive S/N - it was from information captured during the backup at 1am.

The system has 10 HDDs connected, so I had to figure out which physical drive it was.  Basically, using a process of elimination.  I wanted to install some more RAM and upgrade the MB Firmware too, so this was as good a time as any to power down the system and start opening drive bays to see which device was where.  I love hot-swap drive cages.  Took less than 30 seconds to find the missing HDD in an external enclosure.  I have a label on the front of each HDD with the vendor, model, S/N and WWN printed.  Physically seeing that label does require pulling the HDD in the drive caddy, however.

Because the superblock was missing, I assumed that I'd need to run some disk diagnostics. Pull the drive and put it into a USB Dock on another box.  It is found. All partitions found.  Run fsck on all three file systems there - 1 gets some nodes removed, but the other are fine, clean.  Disconnect the dock.

Do the motherboard firmware update and add the RAM to the original system.  Also put the disk back into the external array, but slap it into a different array slot.  Boot the system.  Still missing, just that 1 drive.  I love hot-swap HDDs.  Pull it from 1 slot and move it to a spare.  It isn't seen.  What?  Other drives in that array are working fine.  Time for something drastic.  I pull the HDD from the external array.  Also umount an old, slow, needs-to-be-retired 320G HDD in an drive cage installed in the front of the computer.  Swap the mounting hardware between the 320G and the 4TB HDDs - I'm gonna swap where those are located.  They are completely different brands of HDDs and one is 12+ yrs old.  Internal-cage --> external array and the opposite.  Do that ... and both HDDs are seen.  I have no idea what happened.  I'm assuming the connectors in the newer 4TB are a little thinner than in the older drive and that tiny difference is enough to make the connections not-perfect in the cheap external array.  That's what I get for going cheap, I suppose.

BTW, if this last thing hadn't worked, I'd have taken my backup drive with all the data and made it primary.  My backup disks are USB connected and less than ideal for primary storage, but while I'm waiting for a new disk to arrive via delivery service, having access to the data is more important.  No matter what, this was going to be a minor inconvenience only. No data was lost.

FYI, in case people want to know about the hardware ... 
[LIST]
[*]internal drive cage: [https://www.amazon.com/dp/B00DGZ42SM](https://www.amazon.com/dp/B00DGZ42SM) <--- after 1-2 yrs, I did replace the ban for a Notura silent fan when the internal fan started getting really noisy. There are cheaper and much more expensive versions. This is plastic, but for as stupid as it is, I love it.
[*]Cheap External Array:  [https://www.amazon.com/gp/product/B003X26VV4](https://www.amazon.com/gp/product/B003X26VV4) <--- has some odd issues. Some newer models specifically say they don't support Linux. OTOH, it is $90 now for a 4 drive JBOD array with eSATA-pm!
[/LIST]

I have another external disk array that connects via InfiniBand from Norco.  It was more expensive and has a physical power switch which is very important (the Probox fails this and has bad behavior due to it). Norco has stopped dealing with consumers, so when my array dies (it is 15+ yrs old), I'll need to do something else.

---

