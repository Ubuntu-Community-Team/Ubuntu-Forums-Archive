---
title: "[SOLVED] Missing Hard Drive in Hardy"
date: 2008-06-10
forum: General Help
---

### Post by {}dif{} on 2008-06-10
Hi all,

I'm trying to get Hardy installed on my system which has worked flawlessly with Gutsy and Feisty.

However, when I boot onto the Hardy disc, it doesn't detect any hard drives.  I have an MSI KT4V motherboard (Via KT400 chipset) and a Maxtor 120GB hard drive.  In my still existing Gutsy install, it works just fine.  Googling has found these (which use the same chipset and have the same problem), but they don't have solutions yet:

[http://www.linuxforums.org/forum/ubuntu-help/120022-missing-hard-drive.html](http://www.linuxforums.org/forum/ubuntu-help/120022-missing-hard-drive.html)
[http://www.linuxquestions.org/questions/ubuntu-63/hardy-install-doesnt-find-hard-disk-636614/](http://www.linuxquestions.org/questions/ubuntu-63/hardy-install-doesnt-find-hard-disk-636614/)

The following are from the live Hardy environment:

```
ubuntu@ubuntu:~$ lspci | grep VIA
00:00.0 Host bridge: VIA Technologies, Inc. VT8377 [KT400/KT600 AGP] Host Bridge
00:01.0 PCI bridge: VIA Technologies, Inc. VT8235 PCI Bridge
00:10.0 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 80)
00:10.1 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 80)
00:10.2 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 80)
00:10.3 USB Controller: VIA Technologies, Inc. USB 2.0 (rev 82)
00:11.0 ISA bridge: VIA Technologies, Inc. VT8235 ISA Bridge
00:11.1 IDE interface: VIA Technologies, Inc. VT82C586A/B/VT82C686/A/B/VT823x/A/C PIPC Bus Master IDE (rev 06)
00:11.5 Multimedia audio controller: VIA Technologies, Inc. VT8233/A/8235/8237 AC97 Audio Controller (rev 50)
00:12.0 Ethernet controller: VIA Technologies, Inc. VT6102 [Rhine-II] (rev 74)

```

```
ubuntu@ubuntu:~$ lsmod | grep ata
pata_via               13316  1 
pata_acpi               8320  0 
ata_generic             8324  0 
libata                159344  3 pata_via,pata_acpi,ata_generic
scsi_mod              151436  5 sr_mod,sg,sd_mod,usb_storage,libata
```


Any ideas would be much appreciated.  Thanks!

---

### Post by cariboo on 2008-06-10
Grub is now located on your new partition and it isn't pointing to the right drives. the best thing to do is list your partitons here and we can help you from there. So boot from your live cd and in a terminal enter:

```
sudo fdisk -l
``` 

and paste the result in your next post.

Jim

---

### Post by {}dif{} on 2008-06-11
Thanks for the reply.

I guess I was a little ambiguous though.  In Hardy, there are no hard drives detected.  They don't show up in Ubiquity and `sudo fdisk -l` had no output.  I haven't edited any partitions yet because I can't even access the drive at all.

I do have /dev/sda:
brw-rw----  1 root   disk      8,   0 2008-06-09 08:23 sda
which I found to be a little odd since I can't actually access it.

Thanks again!

---

### Post by garlicsalt2 on 2008-06-14
All, right. I'm going to give this a shot - maybe I can help. I'm gonna' try anyway.

Can you descrive the hardware in question? Specifically, the the type of Interface for the CD-ROM and the HDD. Ie, SCSI, EIDE/ATA/PATA, or SATA, etc.. Is this a custom built system? If it is a pre-built system, then roughly how old is the model? Ie, when did Dell, HP, Gateway, or whomever, consider it "brand new".

I just bought an old Laptop, and had a problem detecting the Hard Drive. I figured out the problem, and solved it. I then did a search to see if anyone else is having the same problem, and turned up this thread.

Lastly, do you know how your hard drive(s) are supposed to be laid out?

I think you said you had Linux installed before, is that correct? Do you know how many partitions you had set-up before??

---

### Post by cariboo on 2008-06-14
The information you have provided so far really doesn't help could post the output of dmesg here. In a terminal tyoe:

```
dmesg | grep ata
```

the pipe | symbol is on the same key as the \

You should see something like this:

```
[    0.000000]  BIOS-e820: 000000007dfd0000 - 000000007dfde000 (ACPI data)
[    0.000000] PERCPU: Allocating 34656 bytes of per cpu data
[   23.501183] Memory: 2022836k/2064192k available (2489k kernel code, 40968k reserved, 1318k data, 320k init)
[   24.260635] Error attaching device data
[   24.260640] Error attaching device data
[   25.877415] libata version 3.00 loaded.
[   26.455013] sata_nv 0000:00:0e.0: version 3.5
[   26.456453] scsi0 : sata_nv
[   26.456718] scsi1 : sata_nv
[   26.456863] ata1: SATA max UDMA/133 cmd 0xd800 ctl 0xd480 bmdma 0xd000 irq 22
[   26.456866] ata2: SATA max UDMA/133 cmd 0xd400 ctl 0xd080 bmdma 0xd008 irq 22
[   26.923174] ata1: SATA link up 1.5 Gbps (SStatus 113 SControl 300)
[   26.930559] ata1.00: ATA-7: HDT722516DLA380, V43OA9BA, max UDMA/133
```

I cut the rest off because this is just an example.

Jim

---

### Post by ikki_72 on 2008-06-14
or you could use sysinfo to get if you're more towards the GUI stuff instead or typing **lspci**, **dmesg** or **lshw**
```
sudo apt-get install sysinfo
```

---

### Post by {}dif{} on 2008-06-14
garlicsalt:
It's a custom build coming on 5 years old.  Primary Master is my Maxtor 120GB drive.  Primary Slave is an offbrand 16x DVD-ROM.  Secondary Master is a offbrand  Norcent CD-RW.  Motherboard is a MSI KT4V.

Currently on my gutsy install, I have 3 partitions.  hda1 ~ 20GB as /, hda2 ~ 1.5GB as swap, and hda3 which fills the rest as /home.  I plan on overwriting hda1 as my root partition on hardy.

cariboo:
```
ubuntu@ubuntu:~$ dmesg | grep ata
[    0.000000]  BIOS-e820: 000000001fff0000 - 000000001fff8000 (ACPI data)
[   52.794756] Memory: 507300k/524224k available (2157k kernel code, 16272k reserved, 998k data, 364k init, 0k highmem)
[   52.794773]       .data : 0xc031b5a4 - 0xc0414dc4   ( 998 kB)
[   56.677038] libata version 3.00 loaded.
[   57.031169] pata_via 0000:00:11.1: version 0.3.3
[   57.032259] scsi0 : pata_via
[   57.033046] scsi1 : pata_via
[   57.035991] ata1: PATA max UDMA/133 cmd 0x1f0 ctl 0x3f6 bmdma 0xfc00 irq 14
[   57.035995] ata2: PATA max UDMA/133 cmd 0x170 ctl 0x376 bmdma 0xfc08 irq 15
[   62.226086] ata1: port is slow to respond, please be patient (Status 0x80)
[   67.039620] ata1: SRST failed (errno=-16)
[   67.371937] ata1.01: ATAPI: IDE!DVD-ROM 1>y"     i "     ) "   !   ", VER(7.72, max UDMA/33
[   67.543541] ata1.01: model number mismatch 'IDE!DVD-ROM 1>y"     i "     ) "   !   "' != 'IDE DVD-ROM 16Y2('
[   67.543545] ata1.01: revalidation failed (errno=-19)
[   67.543552] ata1.01: limiting speed to UDMA/33:PIO3
[   67.543555] ata1: failed to recover some devices, retrying in 5 secs
[   72.884939] ata1.01: model number mismatch 'IDE!DVD-ROM 1>y"     i "     ) "   !   "' != 'IDE"DVD-RO_216X  i   "   !   "   i "   !'
[   72.884946] ata1.01: revalidation failed (errno=-19)
[   72.884951] ata1.01: disabled
[   74.112828] ata2.01: ATAPI: Norcent RWJ-401S, ZSE2, max UDMA/33
[   74.284103] ata2.01: configured for UDMA/33
```

I don't know exactly what to make of this but it seems like my hdd never even responds.  What do you think?

ikki:
I actually prefer CLI's generally but thanks for the tip.  It'll be nice to have something to suggest to others who do prefer GUI's.

---

### Post by {}dif{} on 2008-06-14
Thanks cariboo.  Apparently, since my DVD-ROM drive was slow to respond it was messing up my HDD as well.  Removed my DVD-ROM drive and all is well.  Thanks for the pointers!

---

### Post by PaulEdwards on 2011-04-05
> **{}dif{} said:**
> Thanks cariboo.  Apparently, since my DVD-ROM drive was slow to respond it was messing up my HDD as well.  Removed my DVD-ROM drive and all is well.  Thanks for the pointers!
Thank you for posting this thread.

It helped me diagnose and repair a friend's Windows PC using an Ubuntu 10.10 Live CD.

Disconnecting the IDE DVD drive on her system temporarily resolved the SATA HD not appearing issue in Ubuntu, but it seems to have been a red herring because the real issue turned out to be a faulty SATA port on the motherboard.

Moving the HD to another SATA port resolved all issues.

---

