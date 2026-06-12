---
title: "Problem with Suspend"
date: 2012-11-30
forum: General Help
---

### Post by magnumstyle007 on 2012-11-30
I am fairly new to this, so please excuse if this post is misplaced or incomplete. 
Ubuntu is running pretty smooth on my laptop, but I cannot suspend more than once before restarting and it is really frustrating. When I try to suspend again, it just logs out. 

Please help me out here.


I am running 

Distributor ID:    Ubuntu
Description:    Ubuntu 12.04.1 LTS
Release:    12.04
Codename:    precise

on an X301 Lenovo.

---

### Post by debodas on 2012-11-30
How big is your swap partition? Your swap has to be at least as big as your ram is you want to use suspend properly.

---

### Post by gnusci on 2012-11-30
> **kingnick42 said:**
> How big is your swap partition? Your swap has to be at least as big as your ram is you want to use suspend properly.

Twice is better.

---

### Post by 2F4U on 2012-11-30
> **kingnick42 said:**
> How big is your swap partition? Your swap has to be at least as big as your ram is you want to use suspend properly.

Suspend to RAM doesn't need swap and, in a default Ubuntu installation, hibernation (suspend to disk) is disabled.

> When I try to suspend again, it just logs out. 

Can you take a look into /var/log/pm-suspend.log, which has the debug output of the suspend process in it, and see if there is any hint on errors?
Additionally, it may be helpful if you could provide as much information about your hardware as possible.

---

### Post by magnumstyle007 on 2012-12-01
Thank you for the replies.

The output of sudo lshw -short reads

```

H/W path           Device      Class          Description
=========================================================
                               system         2776LFG ()
/0                             bus            2776LFG
/0/0                           memory         128KiB BIOS
/0/6                           processor      Intel(R) Core(TM)2 Duo CPU     U9400  @ 1.40GHz
/0/6/a                         memory         64KiB L1 cache
/0/6/c                         memory         3MiB L2 cache
/0/b                           memory         64KiB L1 cache
/0/2b                          memory         2GiB System Memory
/0/2b/0                        memory         2GiB SODIMM DDR3 Synchronous 800 MHz (1.2 ns)
/0/2b/1                        memory         SODIMM DDR2 Synchronous 800 MHz (1.2 ns) [empty]
/0/100                         bridge         Mobile 4 Series Chipset Memory Controller Hub
/0/100/2                       display        Mobile 4 Series Chipset Integrated Graphics Controller
/0/100/2.1                     display        Mobile 4 Series Chipset Integrated Graphics Controller
/0/100/3                       communication  Mobile 4 Series Chipset MEI Controller
/0/100/19          eth0        network        82567LM Gigabit Network Connection
/0/100/1a                      bus            82801I (ICH9 Family) USB UHCI Controller #4
/0/100/1a.1                    bus            82801I (ICH9 Family) USB UHCI Controller #5
/0/100/1a.2                    bus            82801I (ICH9 Family) USB UHCI Controller #6
/0/100/1a.7                    bus            82801I (ICH9 Family) USB2 EHCI Controller #2
/0/100/1b                      multimedia     82801I (ICH9 Family) HD Audio Controller
/0/100/1c                      bridge         82801I (ICH9 Family) PCI Express Port 1
/0/100/1c.1                    bridge         82801I (ICH9 Family) PCI Express Port 2
/0/100/1c.1/0      wlan0       network        Ultimate N WiFi Link 5300
/0/100/1d                      bus            82801I (ICH9 Family) USB UHCI Controller #1
/0/100/1d.1                    bus            82801I (ICH9 Family) USB UHCI Controller #2
/0/100/1d.2                    bus            82801I (ICH9 Family) USB UHCI Controller #3
/0/100/1d.7                    bus            82801I (ICH9 Family) USB2 EHCI Controller #1
/0/100/1e                      bridge         82801 Mobile PCI Bridge
/0/100/1f                      bridge         ICH9M-E LPC Interface Controller
/0/100/1f.2        scsi0       storage        82801IBM/IEM (ICH9M/ICH9M-E) 4 port SATA Controller [AHCI mode]
/0/100/1f.2/0      /dev/sda    disk           128GB SAMSUNG MMCQE28G
/0/100/1f.2/0/1    /dev/sda1   volume         25GiB Windows NTFS volume
/0/100/1f.2/0/2    /dev/sda2   volume         5108MiB Windows FAT volume
/0/100/1f.2/0/3    /dev/sda3   volume         88GiB Extended partition
/0/100/1f.2/0/3/5  /dev/sda5   volume         86GiB Linux filesystem partition
/0/100/1f.2/0/3/6  /dev/sda6   volume         1938MiB Linux swap / Solaris partition
/0/100/1f.2/1      /dev/cdrom  disk           DVD-RAM UJ-844
/0/100/1f.3                    bus            82801I (ICH9 Family) SMBus Controller
/1                             power          42T4522
/2                 wwan0       network        Ethernet interface

```

From /var/log/pm-suspend.log,
these lines sound suspicious, but are hieroglyphs to me

```

/usr/lib/pm-utils/sleep.d/49wwan suspend suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/55NetworkManager suspend suspend:
Having NetworkManager put all interaces to sleep...Failed.

/usr/lib/pm-utils/sleep.d/55NetworkManager suspend suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/55wicd suspend suspend:

/usr/lib/pm-utils/sleep.d/55wicd suspend suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/60_wpa_supplicant suspend suspend:
Failed to connect to wpa_supplicant - wpa_ctrl_open: No such file or directory

```

My partitions are 

```

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *          63    53250047    26624992+   7  HPFS/NTFS/exFAT
/dev/sda2       239606640   250069679     5231520   12  Compaq diagnostics
/dev/sda3        53252094   239605759    93176833    5  Extended
/dev/sda5        53252096   235634687    91191296   83  Linux
/dev/sda6       235636736   239605759     1984512   82  Linux swap / Solaris

```

so maybe swap is to small, but then I don t understand why it would work fine the first time after boot?

---

### Post by magnumstyle007 on 2012-12-03
Does this information confirm that the problem is caused by a too small swap partition?

---

### Post by debodas on 2012-12-05
> **magnumstyle007 said:**
> Does this information confirm that the problem is caused by a too small swap partition?

Probably not. Having a look around, it seems to be a problem some others are having, with no current fix.

See [http://ubuntuforums.org/showthread.php?t=1753005](http://ubuntuforums.org/showthread.php?t=1753005)

---

