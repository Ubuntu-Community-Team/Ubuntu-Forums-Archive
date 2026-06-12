---
title: "Cant mount cd drive :'("
date: 2008-03-16
forum: General Help
---

### Post by coninsan on 2008-03-16
hi

im planning to dualboot linux 7.10 and windows xp, to more easaly get to the programs with wine.
But theres one thing standing in my way.
My cd-drive wont mount, im getting this message when i try to acces the drive:
mount: mount point /media/cdrom1 does not exist

heres my greb cd and fstab info if anyone needs it.

grebcd 
[    0.000000] ACPI: FACP 7FE7ECDD, 00F4 (r3 INTEL  CRESTLNE  6040000 ALAN        1)
[   26.837302] ACPI: SSDT 7FE77CD1, 0085 (r1  PmRef  Cpu1Cst     3000 INTL 20050624)

fstab 
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda1
UUID=2ba6bc00-6d55-4c75-8e12-71b199b974c6 /               ext3    defaults,errors=remount-ro 0       1
# /dev/sda5
UUID=77e963c2-9e24-452b-b439-8c04939eac83 none            swap    sw              0       0
/dev/scd0       /media/cdrom1   udf,iso9660 user,noauto,exec 0       0

current problem: 
when i try to acces the drive it says:
mount: special device /dev/scd0 does not exist

---

### Post by coninsan on 2008-03-16
Come on ppl i urgently need help :(

---

### Post by banewman on 2008-03-16
/media/cdrom1 suggests you have two cd drives
If you only have one rewrite the fstab entry to read
/media/cdrom0
:)

---

### Post by coninsan on 2008-03-16
thanks for the reply, just so you know, i installed linux 2 days ago so i am uber noob at it, and i do not know how to get to the fstab file and edit it :(

---

### Post by danwood76 on 2008-03-16
Or you could create the mount point

```

sudo mkdir /media/cdrom1

```

By the way you do this command in the terminal.

---

### Post by coninsan on 2008-03-16
i found my way into the fstab file :)
but i cant edit it, it says, when i try to save and close, that i havnt got the rights to do it.

i also tried 

sudo mkdir /media/cdrom1

but nothing happened. :(

---

### Post by banewman on 2008-03-16
```
gksudo gedit /etc/fstab
```
typed in a terminal will let you save changes made to the fstab file
:)

---

### Post by coninsan on 2008-03-16
that did do a difference but only to get this error showing:

mount: special device /dev/scd0 does not exist

had somewhat of the same problem with my external drive, that one i plugged into a pc with windows xp and disconnected it safely and it worked like a treat, but obviously you cant do that to an internal cd drive.

---

### Post by coninsan on 2008-03-16
is there a way to solve this problem:

mount: special device /dev/scd0 does not exist

ive in the mean time tried to change the fstab info to make it a hdd drive and a few other options but it doesnt work :(

---

### Post by banewman on 2008-03-16
I would - since ubuntu made an entry in fstab for it the cd drive was working before - open the box and check the cables to the cd drive.
Disconnect them and reconnect them to be sure.
:)

---

### Post by coninsan on 2008-03-16
i am running on a laptop, so checking the connections is not really an option, i installed ubuntu friday by using the live cd, and the drive worked perfektly, since then ive reinstalled ubuntu once due to me messing around with something i dont know my way around, and it worked perfectly to then.
its only when i try to acces the drive in ubuntu that i get the error "mount: special device /dev/scd0 does not exist."

i have no idea why it does that.

---

### Post by coninsan on 2008-03-16
anyone?

---

### Post by unutbu on 2008-03-16
coninsan, actually with Ubuntu, sometimes less is more.
Try the following:
```

cp /etc/fstab /etc/fstab.orig

```

This will give you a copy of your fstab, just in case the following doesn't work.
Next, type
```
gksudo gedit /etc/fstab
```

and put a pound sign (#) in front of the line beginning "/dev/scd0": 

```
#/dev/scd0 /media/cdrom1 udf,iso9660 user,noauto,exec 0 0

```

Now reboot. Hopefully, Ubuntu's automounter will detect your CD drive and 
will mount it for you. If this is successful, a Nautilus filemanager window should pop up whenever you insert a CD. No messing around with the command line! If it works, you don't have to read on...

If that doesn't work, then the next thing we'll need to establish is if Gutsy is detecting your hardware. Toward that end, in a terminal window, type
```

sudo lshw -C disk

```
and post the output here (just the part related to the cdrom will do). If you are unsure of which part to post, just post it all.

Also, I notice you wrote
> mount: mount point /media/cdrom1 does not exist


So it would be good for us to see what your /media directory looks like.
Please post the output to
```

ls -l /media

```

---

### Post by coninsan on 2008-03-16
the method you posted Unutbu, did not work. It did make my direktory for my cddrive disapear, and make to drive rev when i put cd's in it.
somewhat of an improvement.

heres the info you wanted
```
coninsan@coninsan-laptop:~$ sudo lshw -C disk
[sudo] password for coninsan:
  *-disk                  
       description: SCSI Disk
       product: ST9160823AS
       vendor: ATA
       physical id: 0.0.0
       bus info: scsi@2:0.0.0
       logical name: /dev/sda
       version: 3.AA
       serial: 5NK06ZQD
       size: 149GB
       capabilities: partitioned partitioned:dos
       configuration: ansiversion=5

```

and 

```
coninsan@coninsan-laptop:~$ ls -l /media
totalt 8
lrwxrwxrwx 1 root root    6 2008-03-15 16:19 cdrom -> cdrom0
drwxr-xr-x 2 root root 4096 2008-03-15 16:19 cdrom0
drwxr-xr-x 2 root root 4096 2008-03-16 11:24 cdrom1

```

at this point im wondering if ubuntu even supports my cd drive.. :(

---

### Post by unutbu on 2008-03-16
Sorry to see the automount trick did not work.
You can return your fstab to its original state if you wish by typing:
```

sudo cp /etc/fstab.orig /etc/fstab

```

It's not going to make much difference however, until your CD drive is detected by Gutsy.
The lshw command shows only your hard drive. Your CD drive should also have been listed. Its absence implies the hardware was not properly detected and the proper driver loaded during the boot process. 

In a terminal type
```

gedit /var/log/messages

```
Read through the messages looking for anything related to the CD-ROM drive. There is a lot of repetition in this file (one for each reboot) so its probably okay to skip everything until you reach the entries dated for today. That might save you some time.
Especially look for any error messages. Post anything you think is relevant here.

It would also help to know the make and model of the CD-ROM drive. You can find that out under Windows XP, or if you boot from the Ubuntu Live CD, run the lshw command again.

---

### Post by coninsan on 2008-03-16
Code:

```
gedit /var/log/messages
```

gave bubkiss, there where no entries marked with cdrom, i only got this that anything to do with the drives.

```
Mar 15 17:31:48 coninsan-laptop kernel: [    5.236000] sd 2:0:0:0: [sda] 312581808 512-byte hardware sectors (160042 MB)
Mar 15 17:31:48 coninsan-laptop kernel: [    5.236000] sd 2:0:0:0: [sda] Write Protect is off
Mar 15 17:31:48 coninsan-laptop kernel: [    5.236000] sd 2:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
Mar 15 17:31:48 coninsan-laptop kernel: [    5.236000] sd 2:0:0:0: [sda] 312581808 512-byte hardware sectors (160042 MB)
Mar 15 17:31:48 coninsan-laptop kernel: [    5.236000] sd 2:0:0:0: [sda] Write Protect is off
Mar 15 17:31:48 coninsan-laptop kernel: [    5.236000] sd 2:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
Mar 15 17:31:48 coninsan-laptop kernel: [    5.236000]  sda:<6>eth0: Tigon3 [partno(BCM95787m) rev b002 PHY(5787)] (PCI Express) 10/100/1000Base-T Ethernet 00:a0:d1:c2:98:42
Mar 15 17:31:48 coninsan-laptop kernel: [    5.252000] eth0: RXcsums[1] LinkChgREG[0] MIirq[0] ASF[0] WireSpeed[1] TSOcap[1]
Mar 15 17:31:48 coninsan-laptop kernel: [    5.252000] eth0: dma_rwctrl[76180000] dma_mask[64-bit]
Mar 15 17:31:48 coninsan-laptop kernel: [    5.276000]  sda1 sda2 < sda5 >
Mar 15 17:31:48 coninsan-laptop kernel: [    5.300000] sd 2:0:0:0: [sda] Attached SCSI disk
```

but anyway, heres what lshw could give me.
```
coninsan@coninsan-laptop:~$ lshw
WARNING: you should run this program as super-user.
coninsan-laptop           
    description: Computer
    width: 32 bits
  *-core
       description: Motherboard
       physical id: 0
     *-memory
          description: System memory
          physical id: 0
          size: 2025MB
     *-cpu
          product: Intel(R) Core(TM)2 Duo CPU     T7500  @ 2.20GHz
          vendor: Intel Corp.
          physical id: 1
          bus info: cpu@0
          version: 6.15.10
          serial: 0000-06FA-0000-0000-0000-0000
          size: 2200MHz
          capacity: 2200MHz
          width: 64 bits
          capabilities: fpu fpu_exception wp vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe nx x86-64 constant_tsc pni monitor ds_cpl vmx est tm2 ssse3 cx16 xtpr lahf_lm cpufreq
          configuration: id=0
        *-logicalcpu:0
             description: Logical CPU
             physical id: 0.1
             width: 64 bits
             capabilities: logical
        *-logicalcpu:1
             description: Logical CPU
             physical id: 0.2
             width: 64 bits
             capabilities: logical
     *-pci
          description: Host bridge
          product: Mobile PM965/GM965/GL960 Memory Controller Hub
          vendor: Intel Corporation
          physical id: 100
          bus info: pci@0000:00:00.0
          version: 03
          width: 32 bits
          clock: 33MHz
        *-pci:0
             description: PCI bridge
             product: Mobile PM965/GM965/GL960 PCI Express Root Port
             vendor: Intel Corporation
             physical id: 1
             bus info: pci@0000:00:01.0
             version: 03
             width: 32 bits
             clock: 33MHz
             capabilities: pci normal_decode bus_master cap_list
             configuration: driver=pcieport-driver
           *-display
                description: VGA compatible controller
                product: GeForce 8600M GT
                vendor: nVidia Corporation
                physical id: 0
                bus info: pci@0000:01:00.0
                version: a1
                width: 64 bits
                clock: 33MHz
                capabilities: vga bus_master cap_list
                configuration: driver=nvidia latency=0 module=nvidia
        *-usb:0
             description: USB Controller
             product: 82801H (ICH8 Family) USB UHCI Contoller #4
             vendor: Intel Corporation
             physical id: 1a
             bus info: pci@0000:00:1a.0
             version: 03
             width: 32 bits
             clock: 33MHz
             capabilities: uhci bus_master
             configuration: driver=uhci_hcd latency=0 module=uhci_hcd
        *-usb:1
             description: USB Controller
             product: 82801H (ICH8 Family) USB UHCI Controller #5
             vendor: Intel Corporation
             physical id: 1a.1
             bus info: pci@0000:00:1a.1
             version: 03
             width: 32 bits
             clock: 33MHz
             capabilities: uhci bus_master
             configuration: driver=uhci_hcd latency=0 module=uhci_hcd
        *-usb:2
             description: USB Controller
             product: 82801H (ICH8 Family) USB2 EHCI Controller #2
             vendor: Intel Corporation
             physical id: 1a.7
             bus info: pci@0000:00:1a.7
             version: 03
             width: 32 bits
             clock: 33MHz
             capabilities: ehci bus_master cap_list
             configuration: driver=ehci_hcd latency=0 module=ehci_hcd
        *-multimedia
             description: Audio device
             product: 82801H (ICH8 Family) HD Audio Controller
             vendor: Intel Corporation
             physical id: 1b
             bus info: pci@0000:00:1b.0
             version: 03
             width: 64 bits
             clock: 33MHz
             capabilities: bus_master cap_list
             configuration: driver=hdaudio latency=0 module=hdaudio
        *-pci:1
             description: PCI bridge
             product: 82801H (ICH8 Family) PCI Express Port 1
             vendor: Intel Corporation
             physical id: 1c
             bus info: pci@0000:00:1c.0
             version: 03
             width: 32 bits
             clock: 33MHz
             capabilities: pci normal_decode bus_master cap_list
             configuration: driver=pcieport-driver
           *-network UNCLAIMED
                description: Network controller
                product: AR5418 802.11a/b/g/n Wireless PCI Express Adapter
                vendor: Atheros Communications, Inc.
                physical id: 0
                bus info: pci@0000:02:00.0
                version: 01
                width: 64 bits
                clock: 33MHz
                capabilities: bus_master cap_list
                configuration: latency=0
        *-pci:2
             description: PCI bridge
             product: 82801H (ICH8 Family) PCI Express Port 2
             vendor: Intel Corporation
             physical id: 1c.1
             bus info: pci@0000:00:1c.1
             version: 03
             width: 32 bits
             clock: 33MHz
             capabilities: pci normal_decode bus_master cap_list
             configuration: driver=pcieport-driver
        *-pci:3
             description: PCI bridge
             product: 82801H (ICH8 Family) PCI Express Port 3
             vendor: Intel Corporation
             physical id: 1c.2
             bus info: pci@0000:00:1c.2
             version: 03
             width: 32 bits
             clock: 33MHz
             capabilities: pci normal_decode bus_master cap_list
             configuration: driver=pcieport-driver
           *-memory UNCLAIMED
                description: Memory controller
                product: Turbo Memory Controller
                vendor: Intel Corporation
                physical id: 0
                bus info: pci@0000:04:00.0
                version: 01
                width: 32 bits
                clock: 33MHz (30.3ns)
                capabilities: bus_master cap_list
                configuration: latency=0
        *-pci:4
             description: PCI bridge
             product: 82801H (ICH8 Family) PCI Express Port 4
             vendor: Intel Corporation
             physical id: 1c.3
             bus info: pci@0000:00:1c.3
             version: 03
             width: 32 bits
             clock: 33MHz
             capabilities: pci normal_decode bus_master cap_list
             configuration: driver=pcieport-driver
           *-network
                description: Ethernet interface
                product: NetLink BCM5787M Gigabit Ethernet PCI Express
                vendor: Broadcom Corporation
                physical id: 0
                bus info: pci@0000:05:00.0
                logical name: eth0
                version: 02
                serial: 00:a0:d1:c2:98:42
                width: 64 bits
                clock: 33MHz
                capabilities: bus_master cap_list ethernet physical
                configuration: broadcast=yes driver=tg3 driverversion=3.77 firmware=5787m-v3.23 ip=192.168.0.125 latency=0 module=tg3 multicast=yes
        *-usb:3
             description: USB Controller
             product: 82801H (ICH8 Family) USB UHCI Controller #1
             vendor: Intel Corporation
             physical id: 1d
             bus info: pci@0000:00:1d.0
             version: 03
             width: 32 bits
             clock: 33MHz
             capabilities: uhci bus_master
             configuration: driver=uhci_hcd latency=0 module=uhci_hcd
        *-usb:4
             description: USB Controller
             product: 82801H (ICH8 Family) USB UHCI Controller #2
             vendor: Intel Corporation
             physical id: 1d.1
             bus info: pci@0000:00:1d.1
             version: 03
             width: 32 bits
             clock: 33MHz
             capabilities: uhci bus_master
             configuration: driver=uhci_hcd latency=0 module=uhci_hcd
        *-usb:5
             description: USB Controller
             product: 82801H (ICH8 Family) USB UHCI Controller #3
             vendor: Intel Corporation
             physical id: 1d.2
             bus info: pci@0000:00:1d.2
             version: 03
             width: 32 bits
             clock: 33MHz
             capabilities: uhci bus_master
             configuration: driver=uhci_hcd latency=0 module=uhci_hcd
        *-usb:6
             description: USB Controller
             product: 82801H (ICH8 Family) USB2 EHCI Controller #1
             vendor: Intel Corporation
             physical id: 1d.7
             bus info: pci@0000:00:1d.7
             version: 03
             width: 32 bits
             clock: 33MHz
             capabilities: ehci bus_master cap_list
             configuration: driver=ehci_hcd latency=0 module=ehci_hcd
        *-pci:5
             description: PCI bridge
             product: 82801 Mobile PCI Bridge
             vendor: Intel Corporation
             physical id: 1e
             bus info: pci@0000:00:1e.0
             version: f3
             width: 32 bits
             clock: 33MHz
             capabilities: pci subtractive_decode bus_master cap_list
           *-pcmcia
                description: CardBus bridge
                product: PCIxx12 Cardbus Controller
                vendor: Texas Instruments
                physical id: 6
                bus info: pci@0000:06:06.0
                version: 00
                width: 32 bits
                clock: 33MHz
                capabilities: pcmcia bus_master cap_list
                configuration: driver=yenta_cardbus latency=176 maxlatency=5 mingnt=192 module=yenta_socket
           *-firewire
                description: FireWire (IEEE 1394)
                product: PCIxx12 OHCI Compliant IEEE 1394 Host Controller
                vendor: Texas Instruments
                physical id: 6.1
                bus info: pci@0000:06:06.1
                version: 00
                width: 32 bits
                clock: 33MHz
                capabilities: ohci bus_master cap_list
                configuration: driver=ohci1394 latency=32 maxlatency=4 mingnt=2 module=ohci1394
           *-storage
                description: Mass storage controller
                product: 5-in-1 Multimedia Card Reader (SD/MMC/MS/MS PRO/xD)
                vendor: Texas Instruments
                physical id: 6.2
                bus info: pci@0000:06:06.2
                version: 00
                width: 32 bits
                clock: 33MHz
                capabilities: storage bus_master cap_list
                configuration: driver=tifm_7xx1 latency=57 maxlatency=4 mingnt=7 module=tifm_7xx1
           *-system
                description: Generic system peripheral
                product: PCIxx12 SDA Standard Compliant SD Host Controller
                vendor: Texas Instruments
                physical id: 6.3
                bus info: pci@0000:06:06.3
                version: 00
                width: 32 bits
                clock: 33MHz
                capabilities: bus_master cap_list
                configuration: driver=sdhci latency=57 maxlatency=4 mingnt=7 module=sdhci
        *-isa
             description: ISA bridge
             product: 82801HEM (ICH8M) LPC Interface Controller
             vendor: Intel Corporation
             physical id: 1f
             bus info: pci@0000:00:1f.0
             version: 03
             width: 32 bits
             clock: 33MHz
             capabilities: isa bus_master cap_list
             configuration: latency=0
        *-ide:0
             description: IDE interface
             product: 82801HBM/HEM (ICH8M/ICH8M-E) IDE Controller
             vendor: Intel Corporation
             physical id: 1f.1
             bus info: pci@0000:00:1f.1
             version: 03
             width: 32 bits
             clock: 33MHz
             capabilities: ide bus_master
             configuration: driver=ata_piix latency=0 module=ata_piix
        *-ide:1
             description: IDE interface
             product: 82801HBM/HEM (ICH8M/ICH8M-E) SATA IDE Controller
             vendor: Intel Corporation
             physical id: 1f.2
             bus info: pci@0000:00:1f.2
             version: 03
             width: 32 bits
             clock: 66MHz
             capabilities: ide bus_master cap_list
             configuration: driver=ata_piix latency=0 module=ata_piix
        *-serial UNCLAIMED
             description: SMBus
             product: 82801H (ICH8 Family) SMBus Controller
             vendor: Intel Corporation
             physical id: 1f.3
             bus info: pci@0000:00:1f.3
             version: 03
             width: 32 bits
             clock: 33MHz
             configuration: latency=0

```

i hope it helps in some way :)

i also found this in the papers i recieved after buying the pc 

SAMSUNG DVD-RW DL 6xx4W/6xx5WD/2xx5W

which must be the cddrive :D

---

### Post by unutbu on 2008-03-16
Did you boot off the Live CD?
If so, please post the output of
```
sudo lshw -C disk
```

---

### Post by coninsan on 2008-03-16
heres the lshw -C disk output.

```
ubuntu@ubuntu:~$ sudo lshw -C disk
  *-cdrom                 
       description: DVD-RAM writer
       product: CDDVDW SN-S082H
       vendor: TSSTcorp
       physical id: 0.1.0
       bus info: scsi@0:0.1.0
       logical name: /dev/cdrom
       logical name: /dev/dvd
       logical name: /dev/scd0
       logical name: /dev/sr0
       version: SB00
       capabilities: removable audio cd-r cd-rw dvd dvd-r dvd-ram
       configuration: ansiversion=5 status=ready
     *-disc
          physical id: 0
          logical name: /dev/cdrom
  *-disk
       description: SCSI Disk
       product: ST9160823AS
       vendor: ATA
       physical id: 0.0.0
       bus info: scsi@2:0.0.0
       logical name: /dev/sda
       version: 3.AA
       serial: 5NK06ZQD
       size: 149GB
       capabilities: partitioned partitioned:dos
       configuration: ansiversion=5

```

---

### Post by coninsan on 2008-03-16
???

---

### Post by unutbu on 2008-03-16
Gosh. I don't know what to tell you.
The good news is Ubuntu is compatible with your DVD drive.
The bad news is I have no idea why the LiveCD sees it but your installed Gutsy doesn't.
Did you use the very same LiveCD to install Gutsy?

If so, I'm stumped.

---

### Post by coninsan on 2008-03-16
Yes i did use the same live cd to install ubuntu and get the info.

ive used it a few times to reinstall linux. and at all times the cd drive was not accesable when in ubuntu. 
i have no idea why it does that, other than the drive being not combatible with linux, but if it is, there must be a fault in the os that makes the drive inaccesible, and that fault must be corrected.
Its the only thing in my way along with my master sound volume, before im fully converted to linux. :(

---

### Post by coninsan on 2008-03-16
i think ive found something: :)

> That's a known bug on 6625wd. You can go around it by, after having installed Ubuntu of course, setting the Secondary/Slave to None in BIOS, It's in the first tab. Just select it and pick None by pressing +.

i found it on this site [HTML]http://ubuntuforums.org/showthread.php?t=599557[/HTML]

but i dont know how to get into the bios..
when i startup a screen appers that when i press F2 grants me acces to the boot sequence amung other things, could that be it?

---

### Post by coninsan on 2008-03-16
it worked like a treat :)

but now the drive just can stop rewing, it sounds like it runs on top speed at all time and shakes alot, it scares me :(
does anyone know a possible remedy for it?

---

### Post by unutbu on 2008-03-16
Hey great! Glad to hear it is working, sorta.
I'm not sure, but maybe this will help?

[http://hektor.umcs.lublin.pl/~mikosmul/computing/tips/cd-rom-speed.html](http://hektor.umcs.lublin.pl/~mikosmul/computing/tips/cd-rom-speed.html)

---

### Post by unutbu on 2008-03-16
[http://forums.techguy.org/hardware/139567-cd-rom-always-spinning.html](http://forums.techguy.org/hardware/139567-cd-rom-always-spinning.html)

suggests the DMA has to be enabled. To do this under linux:

```

hdparm -d1 /dev/scd0

```

Although I think the above is safe, please note that hdparm is a dangerous program, so you should read 
```
man hdparm
```
before using it!

---

### Post by staib on 2008-03-16
> **coninsan said:**
> hi
current problem: 
when i try to acces the drive it says:
mount: special device /dev/scd0 does not exist
You are not alone!   I have an identical problem on a Lenovo 3000 N200 laptop. I was dual booting fine last year until I realised that the DVDRW unit was not working in either Ubuntu OR Vista.  Re-installed Vista and all was well again.  Got fed up with slow Vista and re-installed Ubuntu on entire drive.  But same problem...  
LiveCD's work OK - so its not mechanical or a connection - but otherwise the error message stops any further progress.  I hope we get some answers soon  :)

---

### Post by coninsan on 2008-03-17
setting slave to none in bios di the trick for me, accept the drive revs a bit to uch with some cds/dvds.
only real bad thing about it is that, because i now have a dual boot, i have to switch it from slave and back to cdrom, or els it wont really work in xp and it is not possible to mount from a cd/dvd when slave is set to none. 

but otherwise, an easy solution to a semi complicated problem :)

---

