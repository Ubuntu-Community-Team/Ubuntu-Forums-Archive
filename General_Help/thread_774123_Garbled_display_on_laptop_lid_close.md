---
title: "Garbled display on laptop lid close"
date: 2008-04-29
forum: General Help
---

### Post by john91 on 2008-04-29
Hey everyone,

I've done a clean install of hardy, and most everything works great.  However, whenever I close the lid (and this didn't happen w/ hardy beta), my screen becomes a garbled display of colorful blocks.  I can get out of it by switching to another virtual terminal (Ctrl+Alt+F1,F2,etc) and then back.  However, considering I often close my lid during classes, this could become a major inconvenience.  I've got to head off to class right now, but the second I get a chance I'll post whatever info you need to help me.

Thanks,

John

I'm running a IBM Thinkpad T60p, with these hardware specs:

```
mcleanj@mcleanj:~$ sudo lshw -short
H/W path               Device      Class       Description
==========================================================
                                   system      8741AD5
/0                                 bus         8741AD5
/0/0                               memory      144KiB BIOS
/0/6                               processor   Intel(R) Core(TM)2 CPU         T7
/0/6/a                             memory      64KiB L1 cache
/0/6/c                             memory      4MiB L2 cache
/0/b                               memory      64KiB L1 cache
/0/29                              memory      2GiB System Memory
/0/29/0                            memory      1GiB SODIMM Synchronous
/0/29/1                            memory      1GiB SODIMM Synchronous
/0/100                             bridge      Mobile 945GM/PM/GMS, 943/940GML a
/0/100/1                           bridge      Mobile 945GM/PM/GMS, 943/940GML a
/0/100/1/0                         display     M56GL [Mobility FireGL V5250]
/0/100/1b                          multimedia  82801G (ICH7 Family) High Definit
/0/100/1c                          bridge      82801G (ICH7 Family) PCI Express 
/0/100/1c/0                        network     82573L Gigabit Ethernet Controlle
/0/100/1c.1                        bridge      82801G (ICH7 Family) PCI Express 
/0/100/1c.1/0          wifi0       network     AR5212 802.11abg NIC
/0/100/1c.2                        bridge      82801G (ICH7 Family) PCI Express 
/0/100/1c.3                        bridge      82801G (ICH7 Family) PCI Express 
/0/100/1d                          bus         82801G (ICH7 Family) USB UHCI Con
/0/100/1d.1                        bus         82801G (ICH7 Family) USB UHCI Con
/0/100/1d.2                        bus         82801G (ICH7 Family) USB UHCI Con
/0/100/1d.3                        bus         82801G (ICH7 Family) USB UHCI Con
/0/100/1d.7                        bus         82801G (ICH7 Family) USB2 EHCI Co
/0/100/1e                          bridge      82801 Mobile PCI Bridge
/0/100/1e/0                        bridge      PCI1510 PC card Cardbus Controlle
/0/100/1f                          bridge      82801GBM (ICH7-M) LPC Interface B
/0/100/1f.1            scsi4       storage     82801G (ICH7 Family) IDE Controll
/0/100/1f.1/0.0.0      /dev/cdrom  disk        DVDRAM GSA-4083N
/0/100/1f.2            scsi0       storage     82801GBM/GHM (ICH7 Family) SATA A
/0/100/1f.2/0.0.0      /dev/sda    disk        160GB ST9160821AS
/0/100/1f.2/0.0.0/1    /dev/sda1   volume      50GiB EXT3 volume
/0/100/1f.2/0.0.0/2    /dev/sda2   volume      74GiB EXT3 volume
/0/100/1f.2/0.0.0/3    /dev/sda3   volume      23GiB EXT3 volume
/0/100/1f.2/0.0.0/4    /dev/sda4   volume      956MiB Extended partition
/0/100/1f.2/0.0.0/4/5  /dev/sda5   volume      956MiB Linux swap / Solaris parti
/0/100/1f.3                        bus         82801G (ICH7 Family) SMBus Contro
mcleanj@mcleanj:~$ 

```

---

### Post by skymera on 2008-04-29
I think it's common with laptops.

My laptop with a Via graphics chipset does it when i shutdown, switch to a TTY or close the lid.

It hasn't bothered me so i haven't looked for a solution 

Since you have the 945 Intel chipset try using the Intel driver.

its in the repos
```
 sudo apt-get istall xserver-xorg-video-intel 
```

Then reconfigure X to use that driver.
Hope everything works well

---

### Post by john91 on 2008-04-30
I've already installed that driver, and it hasn't done much.  However, I haven't configured anything, and video issues isn't my forte.  Any suggestions would be excellent, and i can post any file/command outputs you need to help me.

---

### Post by john91 on 2008-04-30
bump.

---

### Post by john91 on 2008-04-30
bump.

---

