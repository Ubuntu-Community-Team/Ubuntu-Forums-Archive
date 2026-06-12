---
title: "Lubuntu does not shutdown"
date: 2015-03-22
forum: General Help
---

### Post by andfree on 2015-03-22
This problem affects me on Lubuntu 14.04 LTS, on Lubuntu 14.10, even on non-pae 12.04 mini.iso with Lubuntu Desktop. I never had this problem on Ubuntu Desktop, so I think that it has to do with the Lubuntu Desktop.

**On Lubuntu 14.04 LTS:**

It doesn’t shutdown (and also doesn’t reboot). It begins to shutdown, until the point with Lubuntu logo in the dark blue screen. It never passes this point to complete the shutdown. The screen shows constantly the Lubuntu logo and nothing after that happens. At this point, if I open tty1, it asks me for login, but I can type nothing, it's frozen. (If I open the tty1 other time, before the shutdown attempt, I can type and login with no problem). Finally, I shutdown by keeping pressed the power button or I restart by the Alt+SysRq+type "reisub" combination.

I have exactly the same result if i press shutdown/restart from the shutdown menu or with the commands

```
sudo reboot
sudo poweroff
sudo shutdown -h now
sudo shutdown -r now
```

I tried one by one the following boot option:

```
acpi=off
noapic
nolapic
```

and also this:

[http://askubuntu.com/questions/162211/shutdown-does-not-depower](http://askubuntu.com/questions/162211/shutdown-does-not-depower)

All these attempts had the same results:

1. Reboot from the menu seems to work (I say "seems" because there's a feeling that it shuts down a little quickly and noisily, but maybe it's just my idea. Anyway, the system reboots when I click to do so from the menu).

2. Shutdown from the menu (or "sudo poweroff") stops again at the black screen with lubuntu logo. But, before boot-repairing, the five dots under the logo went on changing colour from white to blue vice versa indefinitely and I could reboot with "reisub" combination. After boot-repairing, the five dots stop to change colours (2 froze in blue & 3 in white, I think) and the "reisub" doesn't work at this point, so I shutdown only by the button.

**On Lubuntu 14.10:**

Exactly the same problems but instead of the dark blue screen with Lubuntu logo, I get into a black screen with some messages.

Every time I get the message:

```
Killing all remaining processes... [fail]
```

Sometimes I get more messages, like these:

```
ModemManager[665]: <warn> Could not acquire the 'org.freedesktop.ModemManager1' service name
```

```
nm-dispatcher.action: Could not get the system bus. Make sure the message bus daemon is running! Message: Did not receive a reply. Possible causes include: the remote application did not send a reply, the message bus security policy blocked the reply, the  reply timeout expired, or the network connection was broken.
```

After some time passes, a continuous line of messages like these appears:

```
INFO : task upowerd:1868 blocked for more than 120 seconds.
               Tainted: G S         3.16.0-31-generic #43-Ubuntu
"echo 0 > /proc/sys/kernel/hung_task_timeout_secs" disables this message.

INFO : task reboot:2388 blocked for more than 120 seconds.
               Tainted: G S         3.16.0-31-generic #43-Ubuntu
"echo 0 > /proc/sys/kernel/hung_task_timeout_secs" disables this message.
```

Finally, I shutdown by keeping pressed the power button or I restart by the Alt+SysRq+type "reisub" combination, again.

I have the same results if I do a logout before shutdown/reboot.

The following commands didn't help:

```
sudo service network-manager stop 
sudo apt-get remove modemmanager
```

Updating didn't help:

```
sudo apt-get update
sudo apt-get dist-upgrade
```

I removed "quiet splash" parametres from /etc/default/grub and uncommented the

```
#GRUB_TERMINAL=console
```

but the only new message I got at shutting down was:

```
nm-dispatcher.action: Could not acquire the org.freedesktop.nm_dispatcher service.
Message: 'Disconnected from D-Bus (or argument error during call)' nm-dispatcher.action: Disconnected from the system bus exiting.

```

And another one message with "nolapic" option:

```
nm-dispatcher.action: Could not get the system bus. Make sure the message bus daemon is running!  Message: Failed to connect to socket /var/run/dbus/system_bus_socket: No such file or directory
```

Some more terminal displays:

```
~$ ls  /etc/systemd/system/ | grep patcher
dbus-org.freedesktop.nm-dispatcher.service
~$ ls /etc/dbus-1/system.d/ | grep patcher
nm-dispatcher.conf
~$ ls /usr/share/dbus-1/system-services | grep patcher
org.freedesktop.nm_dispatcher.service
```

Finally, two *Errors* I get at the final stage of boot (just before enter to the Lubuntu Desktop):

```
drm_i9xx_check_fifo_underruns
drm_i9xx_set_fifo_underrun_reporting
```

The computer description:

```
computer
    description: Notebook
    product: Satellite L10
    vendor: TOSHIBA
    version: PSL10E-021011GE
    serial: [REMOVED]
    width: 32 bits
    capabilities: smbios-2.31 dmi-2.31
    configuration: boot=oem-specific chassis=notebook uuid=[REMOVED]
  *-core
       description: Motherboard
       product: Satellite L10
       vendor: TOSHIBA
       physical id: 0
       version: Rev 1.0
       serial: [REMOVED]
     *-firmware
          description: BIOS
          vendor: TOSHIBA
          physical id: 0
          version: V2.40
          date: 06/22/2005
          size: 107KiB
          capacity: 448KiB
          capabilities: isa pci pcmcia pnp apm upgrade shadowing escd cdboot int13floppy720 int5printscreen int9keyboard int14serial int17printer acpi usb smartbattery biosbootspecification
     *-cpu
          description: CPU
          product: Intel(R) Pentium(R) M processor 1.70GHz
          vendor: Intel Corp.
          physical id: 4
          bus info: cpu@0
          version: 6.13.6
          slot: uFCPGA2
          size: 1700MHz
          capacity: 1700MHz
          width: 32 bits
          clock: 400MHz
          capabilities: fpu fpu_exception wp vme de pse tsc msr pae mce cx8 sep mtrr pge mca cmov clflush dts acpi mmx fxsr sse sse2 ss tm pbe bts est tm2 cpufreq
        *-cache:0
             description: L1 cache
             physical id: 8
             slot: L1 Cache
             size: 32KiB
             capacity: 32KiB
             capabilities: asynchronous internal write-back
        *-cache:1
             description: L2 cache
             physical id: 9
             slot: L2 Cache
             size: 2MiB
             capacity: 2MiB
             capabilities: burst external write-back
     *-memory
          description: System Memory
          physical id: 10
          slot: System board or motherboard
          size: 1GiB
          capacity: 3GiB
        *-bank:0
             description: DIMM SRAM Synchronous 333 MHz (3.0 ns)
             physical id: 0
             slot: DIMM 0
             size: 512MiB
             width: 64 bits
             clock: 333MHz (3.0ns)
        *-bank:1
             description: DIMM SRAM Synchronous 333 MHz (3.0 ns)
             physical id: 1
             slot: DIMM 1
             size: 512MiB
             width: 64 bits
             clock: 333MHz (3.0ns)
     *-pci
          description: Host bridge
          product: 82852/82855 GM/GME/PM/GMV Processor to I/O Controller
          vendor: Intel Corporation
          physical id: 100
          bus info: pci@0000:00:00.0
          version: 02
          width: 32 bits
          clock: 33MHz
          configuration: driver=agpgart-intel
          resources: irq:0
        *-generic:0 UNCLAIMED
             description: System peripheral
             product: 82852/82855 GM/GME/PM/GMV Processor to I/O Controller
             vendor: Intel Corporation
             physical id: 0.1
             bus info: pci@0000:00:00.1
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: bus_master
             configuration: latency=0
        *-generic:1 UNCLAIMED
             description: System peripheral
             product: 82852/82855 GM/GME/PM/GMV Processor to I/O Controller
             vendor: Intel Corporation
             physical id: 0.3
             bus info: pci@0000:00:00.3
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: bus_master
             configuration: latency=0
        *-display:0
             description: VGA compatible controller
             product: 82852/855GM Integrated Graphics Device
             vendor: Intel Corporation
             physical id: 2
             bus info: pci@0000:00:02.0
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: pm vga_controller bus_master cap_list rom
             configuration: driver=i915 latency=0
             resources: irq:6 memory:e8000000-efffffff memory:e0000000-e007ffff ioport:1800(size=8)
        *-display:1 UNCLAIMED
             description: Display controller
             product: 82852/855GM Integrated Graphics Device
             vendor: Intel Corporation
             physical id: 2.1
             bus info: pci@0000:00:02.1
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: pm bus_master cap_list
             configuration: latency=0
             resources: memory:f0000000-f7ffffff memory:e0080000-e00fffff
        *-usb:0
             description: USB controller
             product: 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #1
             vendor: Intel Corporation
             physical id: 1d
             bus info: pci@0000:00:1d.0
             version: 03
             width: 32 bits
             clock: 33MHz
             capabilities: uhci bus_master
             configuration: driver=uhci_hcd latency=0
             resources: irq:6 ioport:1820(size=32)
        *-usb:1
             description: USB controller
             product: 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #2
             vendor: Intel Corporation
             physical id: 1d.1
             bus info: pci@0000:00:1d.1
             version: 03
             width: 32 bits
             clock: 33MHz
             capabilities: uhci bus_master
             configuration: driver=uhci_hcd latency=0
             resources: irq:6 ioport:1840(size=32)
        *-usb:2
             description: USB controller
             product: 82801DB/DBM (ICH4/ICH4-M) USB2 EHCI Controller
             vendor: Intel Corporation
             physical id: 1d.7
             bus info: pci@0000:00:1d.7
             version: 03
             width: 32 bits
             clock: 33MHz
             capabilities: pm debug ehci bus_master cap_list
             configuration: driver=ehci-pci latency=0
             resources: irq:10 memory:e0100000-e01003ff
        *-pci
             description: PCI bridge
             product: 82801 Mobile PCI Bridge
             vendor: Intel Corporation
             physical id: 1e
             bus info: pci@0000:00:1e.0
             version: 83
             width: 32 bits
             clock: 33MHz
             capabilities: pci normal_decode bus_master
             resources: ioport:3000(size=4096) memory:e0200000-e04fffff memory:40000000-43ffffff
           *-pcmcia
                description: CardBus bridge
                product: PCI1410 PC card Cardbus Controller
                vendor: Texas Instruments
                physical id: 1
                bus info: pci@0000:02:01.0
                version: 02
                width: 32 bits
                clock: 33MHz
                capabilities: pcmcia bus_master cap_list
                configuration: driver=yenta_cardbus latency=176 maxlatency=5 mingnt=192
                resources: irq:10 memory:e0400000-e0400fff ioport:3000(size=256) ioport:3400(size=256) memory:40000000-43ffffff memory:e4000000-e7ffffff
           *-network:0
                description: Ethernet interface
                product: RTL-8100/8101L/8139 PCI Fast Ethernet Adapter
                vendor: Realtek Semiconductor Co., Ltd.
                physical id: 2
                bus info: pci@0000:02:02.0
                logical name: eth0
                version: 10
                serial: [REMOVED]
                size: 100Mbit/s
                capacity: 100Mbit/s
                width: 32 bits
                clock: 33MHz
                capabilities: pm bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
                configuration: autonegotiation=on broadcast=yes driver=8139too driverversion=0.9.28 duplex=full ip=[REMOVED] latency=64 link=yes maxlatency=64 mingnt=32 multicast=yes port=MII speed=100Mbit/s
                resources: irq:6 ioport:3800(size=256) memory:e0402000-e04020ff
           *-network:1 DISABLED
                description: Wireless interface
                product: PRO/Wireless 2200BG [Calexico2] Network Connection
                vendor: Intel Corporation
                physical id: 4
                bus info: pci@0000:02:04.0
                logical name: eth1
                version: 05
                serial: [REMOVED]
                width: 32 bits
                clock: 33MHz
                capabilities: pm bus_master cap_list ethernet physical wireless
                configuration: broadcast=yes driver=ipw2200 driverversion=1.2.2kmprq firmware=ABG:9.0.5.27 (Dec 12 2007) latency=64 link=no maxlatency=24 mingnt=3 multicast=yes wireless=IEEE 802.11bg
                resources: irq:11 memory:e0401000-e0401fff
        *-isa
             description: ISA bridge
             product: 82801DBM (ICH4-M) LPC Interface Bridge
             vendor: Intel Corporation
             physical id: 1f
             bus info: pci@0000:00:1f.0
             version: 03
             width: 32 bits
             clock: 33MHz
             capabilities: isa bus_master
             configuration: driver=lpc_ich latency=0
             resources: irq:0
        *-ide
             description: IDE interface
             product: 82801DBM (ICH4-M) IDE Controller
             vendor: Intel Corporation
             physical id: 1f.1
             bus info: pci@0000:00:1f.1
             version: 03
             width: 32 bits
             clock: 33MHz
             capabilities: ide bus_master
             configuration: driver=ata_piix latency=0
             resources: irq:6 ioport:1f0(size=8) ioport:3f6 ioport:170(size=8) ioport:376 ioport:1810(size=16) memory:44000000-440003ff
        *-serial UNCLAIMED
             description: SMBus
             product: 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) SMBus Controller
             vendor: Intel Corporation
             physical id: 1f.3
             bus info: pci@0000:00:1f.3
             version: 03
             width: 32 bits
             clock: 33MHz
             configuration: latency=0
             resources: ioport:1860(size=32)
        *-multimedia
             description: Multimedia audio controller
             product: 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) AC'97 Audio Controller
             vendor: Intel Corporation
             physical id: 1f.5
             bus info: pci@0000:00:1f.5
             version: 03
             width: 32 bits
             clock: 33MHz
             capabilities: pm bus_master cap_list
             configuration: driver=snd_intel8x0 latency=0
             resources: irq:11 ioport:1c00(size=256) ioport:1880(size=64) memory:e0100c00-e0100dff memory:e0100800-e01008ff
        *-communication UNCLAIMED
             description: Modem
             product: 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) AC'97 Modem Controller
             vendor: Intel Corporation
             physical id: 1f.6
             bus info: pci@0000:00:1f.6
             version: 03
             width: 32 bits
             clock: 33MHz
             capabilities: pm generic cap_list
             configuration: latency=0
             resources: ioport:2400(size=256) ioport:2000(size=128)
     *-scsi:0
          physical id: 1
          logical name: scsi0
          capabilities: emulated
        *-disk
             description: ATA Disk
             product: TOSHIBA MK6025GA
             vendor: Toshiba
             physical id: 0.0.0
             bus info: scsi@0:0.0.0
             logical name: /dev/sda
             version: 0U
             serial: [REMOVED]
             size: 55GiB (60GB)
             capabilities: partitioned partitioned:dos
             configuration: ansiversion=5 sectorsize=512 signature=44d92a24
           *-volume:0
                description: EXT4 volume
                vendor: Linux
                physical id: 1
                bus info: scsi@0:0.0.0,1
                logical name: /dev/sda1
                logical name: /
                version: 1.0
                serial: [REMOVED]
                size: 54GiB
                capacity: 54GiB
                capabilities: primary bootable journaled extended_attributes large_files huge_files dir_nlink recover extents ext4 ext2 initialized
                configuration: created=2015-03-09 14:20:20 filesystem=ext4 lastmountpoint=/ modified=2015-03-09 23:24:49 mount.fstype=ext4 mount.options=rw,relatime,errors=remount-ro,data=ordered mounted=2015-03-09 23:24:50 state=mounted
           *-volume:1
                description: Extended partition
                physical id: 2
                bus info: scsi@0:0.0.0,2
                logical name: /dev/sda2
                size: 1005MiB
                capacity: 1005MiB
                capabilities: primary extended partitioned partitioned:extended
              *-logicalvolume
                   description: Linux swap / Solaris partition
                   physical id: 5
                   logical name: /dev/sda5
                   capacity: 1005MiB
                   capabilities: nofs
     *-scsi:1
          physical id: 2
          logical name: scsi1
          capabilities: emulated
        *-cdrom
             description: DVD-RAM writer
             product: DVD-RAM UJ-831S
             vendor: MATSHITA
             physical id: 0.0.0
             bus info: scsi@1:0.0.0
             logical name: /dev/cdrom
             logical name: /dev/cdrw
             logical name: /dev/dvd
             logical name: /dev/dvdrw
             logical name: /dev/sr0
             logical name: /media/popi/Plop Boot Manager 5.0.14
             version: 1.90
             capabilities: removable audio cd-r cd-rw dvd dvd-r dvd-ram
             configuration: ansiversion=5 mount.fstype=iso9660 mount.options=ro,nosuid,nodev,relatime,uid=1000,gid=1000,iocharset=utf8,mode=0400,dmode=0500 state=mounted status=ready
           *-medium
                physical id: 0
                logical name: /dev/cdrom
                logical name: /media/popi/Plop Boot Manager 5.0.14
                configuration: mount.fstype=iso9660 mount.options=ro,nosuid,nodev,relatime,uid=1000,gid=1000,iocharset=utf8,mode=0400,dmode=0500 state=mounted
     *-scsi:2
          physical id: 3
          bus info: usb@1:1
          logical name: scsi2
          capabilities: emulated scsi-host
          configuration: driver=usb-storage
        *-disk
             description: SCSI Disk
             physical id: 0.0.0
             bus info: scsi@2:0.0.0
             logical name: /dev/sdb
             size: 3695MiB (3874MB)
             configuration: sectorsize=512 signature=8852edcf
  *-battery
       description: Lithium Ion Battery
       product: Sanyo
       vendor: Sanyo
       physical id: 1
       slot: Right Side
       capacity: 4400mWh
       configuration: voltage=14.8V
```

---

### Post by Dreamer Fithp Apprentice on 2015-03-22
I haven't a clue how to fix that but I have an idea that might generate information useful to pursuing the fix. How about this:

Install something like lxtask.
Open it up. Kill something. Make a note of what you killed.
Close all windows except for 1 terminal emulator.
sudo shutdown -h now

Do this repeatedly, killing a different process each time. Maybe with luck you'll find some process that is screwing up the shutdown. Maybe not, but if you do you'll at least know what to look closer at. Good luck.

---

### Post by andfree on 2015-03-22
> **Dreamer Fithp Apprentice said:**
> Install something like lxtask.
Open it up. Kill something. Make a note of what you killed.
Close all windows except for 1 terminal emulator.
sudo shutdown -h now

Do this repeatedly, killing a different process each time. Maybe with luck you'll find some process that is screwing up the shutdown. Maybe not, but if you do you'll at least know what to look closer at. Good luck.

Thanks for the reply. I killed at once all I could (some of them appeared again just after I killed them). I killed dbus-daemon & init separately because when I killed one of them I logged out. But after all attempts, it never did a successful shutdown.

---

### Post by kerry_s on 2015-03-22
you missed-> acpi=force
try that

---

### Post by andfree on 2015-03-22
> **kerry_s said:**
> you missed-> acpi=force
try that

Boot-repair doesn't give me this option. I tried it manually (tell me if I made any mistake):

I edited /etc/default/grub like this:

GRUB_CMDLINE_LINUX_DEFAULT="quiet splash acpi=force"

I ran:

sudo update-grub

Then I tried to shutdown, but nothing different happened.

---

### Post by sudodus on 2015-03-22
Did you try Xubuntu 14.04 LTS?

---

### Post by anthonyjeswald on 2015-03-22
I'm having this exact same issue and computer behaviour in Ubuntu Studio 14.04! I should add that it does the same thing from the LiveCD.

---

### Post by sudodus on 2015-03-22
That would indicate, that Xubuntu (with the same desktop environment as Studio) is also affected by the problem, and I would think it is a kernel or driver problem, not a problem with the desktop environment. But your computers are probably different, so you could have different problems, but the same symptom.

---

### Post by anthonyjeswald on 2015-03-22
Thanks, sudodus! What would recommend? Should I try a different flavor? Edited to add: I'm burning a LiveCD of regular Ubuntu 14.10, and I'll give that a try.

---

### Post by kerry_s on 2015-03-22
try installing intel-microcode

sudo apt-get install intel-microcode

reboot 2x, to make sure any firmware upgrade loads.

---

### Post by sudodus on 2015-03-22
If you want Ubuntu Studio, you should try to make it work properly or at least flush the buffers (write everything to disk before shutting down). One way to do it is to run the command

```
sync
```

before you try to shutdown. It could be done in a script or alias, that you use instead of 'the button'.

```
sync; sudo poweroff
```

If you can turn off the power with a short tap on the power button, things are actually OK. The processes are halted, but the machine does not understand, that you want to turn off the power.

If you have to press the power button for several seconds, there are still processes running, which is not nice. Sooner or later (maybe rather soon) you might damage the file system and get big problems unless you have a good backup.

-o-

If the problems persist, you can try another version (12.04 LTS for old systems, 14.10 or even Vivid (still at beta testing) for very new systems). If still problems, you can try another linux distro.

---

### Post by andfree on 2015-03-22
> **sudodus said:**
> Did you try Xubuntu 14.04 LTS?

I can't install it (and every 14.04.2-desktop-i386.iso. I have installed lubuntu-14.04-alternate-i386.iso, but I don't find any xubuntu-14.04-alternate-i386.iso).  

When I try to install Xubuntu 14.04 LTS (and every 14.04.2-desktop-i386.iso) by using the 2 x forcepae, it gets me to a live session with the Install icon on the Desktop. Live session seems to work fine, but when I double-click on the install icon, the cursor spins for a while and stops, and nothing else happens.

&#65279;But as regards the "not shutdown" problem, I see that affects me on the xubuntu live session, too.

---

### Post by kerry_s on 2015-03-22
i'm going for xubuntu 15 on my Toshiba t135 laptop today. been running it on my main pc, seems good enough already.
i been waiting for a friend to bring me a sata sdcard adapter to use as a hd, been running from the sdcard slot for about a week now. currently have xubuntu 14lts on it.

---

### Post by kerry_s on 2015-03-22
did you try the intel-microcode ?

---

### Post by anthonyjeswald on 2015-03-22
> **kerry_s said:**
> try installing intel-microcode

sudo apt-get install intel-microcode

reboot 2x, to make sure any firmware upgrade loads.

Yikes, I've totally threadjacked this discussion. I tried the above, but the behavior is the same. Btw, I tried everything the OP tried as well, but it's still doing it. Maybe I should try going back to 12.04?

---

### Post by sudodus on 2015-03-22
> **andfree said:**
> I can't install it (and every 14.04.2-desktop-i386.iso. I have installed lubuntu-14.04-alternate-i386.iso, but I don't find any xubuntu-14.04-alternate-i386.iso).  

When I try to install Xubuntu 14.04 LTS (and every 14.04.2-desktop-i386.iso) by using the 2 x forcepae, it gets me to a live session with the Install icon on the Desktop. Live session seems to work fine, but when I double-click on the install icon, the cursor spins for a while and stops, and nothing else happens.

&#65279;But as regards the "not shutdown" problem, I see that affects me on the xubuntu live session, too.

The alternate way to install Xubuntu is via the Ubuntu mini.iso, but it would probably not solve the shutdown problem.

Is it necessary to press the power button for several seconds, or is it enough with a short tap?

---

### Post by kerry_s on 2015-03-22
it's so strange it's only shutdown. what about hibernate ? does that power off ?

---

### Post by andfree on 2015-03-22
> **kerry_s said:**
> sudo apt-get install intel-microcode

reboot 2x, to make sure any firmware upgrade loads.

It didn't help, at least for me. The reisub combination was needed both of times to reboot.

---

### Post by anthonyjeswald on 2015-03-22
> **sudodus said:**
> ```
sync
```

before you try to shutdown. It could be done in a script or alias, that you use instead of 'the button'.

```
sync; sudo poweroff
```

If you can turn off the power with a short tap on the power button, things are actually OK. The processes are halted, but the machine does not understand, that you want to turn off the power.

If you have to press the power button for several seconds, there are still processes running, which is not nice. Sooner or later (maybe rather soon) you might damage the file system and get big problems unless you have a good backup.

-o-

If the problems persist, you can try another version (12.04 LTS for old systems, 14.10 or even Vivid (still at beta testing) for very new systems). If still problems, you can try another linux distro.

Thanks, but yeah, I tried the above and still had to hold the power button down (the fan was racing, too). I do have a good backup (and my home directory in a separate partition), but maybe I should go back to 12.04, which was working very well.

I'd still like to try it with a current Ubuntu, though. And by the way, the LiveDVD of vanilla Ubuntu 14.10 does the same behavior.

---

### Post by anthonyjeswald on 2015-03-22
> **kerry_s said:**
> it's so strange it's only shutdown. what about hibernate ? does that power off ?

I don't know about andfree, but I can't even select hibernate.

Btw, REISUB won't work for me, either -- edited to add, when it's frozen, that is. REISUB works to reboot when I'm logged into my profile.

---

### Post by sudodus on 2015-03-22
Yes, stay with / go back to ***12.04 LTS***, which works for you. But you must select a flavour that is supported. (Lubuntu is long gone. Xubuntu will reach end of life in April this year.)

Standard Ubuntu and Kubuntu will be supported until April 2017. The community re-spins Bento, Bodhi and LXLE also promise support until April 2017. Another light alternative is [Precise Gnome Classic Tweaks]("https://help.ubuntu.com/community/PreciseGnomeClassicTweaks").

---

### Post by andfree on 2015-03-22
> **sudodus said:**
> Is it necessary to press the power button for several seconds, or is it enough with a short tap?

Several seconds.

---

### Post by sudodus on 2015-03-22
That is not good. You should really focus on some other version or distro.

---

### Post by andfree on 2015-03-22
> **kerry_s said:**
> what about hibernate ?

Suspend seems to works fine. But on hibernate I get this:

```
GDBus.Error:org.freedesktop.DBus.Error.AccessDenied: Operation not permitted
```

I don't have a battery, I don't know if it has nothing to do with it.

---

### Post by kerry_s on 2015-03-22
did you use "sudo pm-hibernate"

mine doesn't seem to work right, it does the shutdown, but starting up again it reboots, then does a normal start, like it crashed.

---

### Post by anthonyjeswald on 2015-03-22
Well, I just reinstalled 12.04.5, and it's working (and shutting down) perfectly. It must be something in the 14.x kernel. Should I put something up on askubuntu.com?

---

### Post by kerry_s on 2015-03-22
> **anthonyjeswald said:**
> Well, I just reinstalled 12.04.5, and it's working (and shutting down) perfectly. It must be something in the 14.x kernel. Should I put something up on askubuntu.com?

if it works stay with it, it's supported for another 2 years.
my favorite version 12 lts is elementary os luna

---

### Post by andfree on 2015-03-23
> **kerry_s said:**
> did you use "sudo pm-hibernate"

This did nothing at all.

Edit my post [#24]("http://ubuntuforums.org/showthread.php?t=2270322&p=13250586#post13250586") :

Hibernate from menu seems to work. But when I move the mouse and then login, I see the shutdown menu window with that error message at the bottom.

---

### Post by sudodus on 2015-03-23
> **anthonyjeswald said:**
> Well, I just reinstalled 12.04.5, and it's working (and shutting down) perfectly. It must be something in the 14.x kernel. Should I put something up on askubuntu.com?

Yes, if you wish, you can try that. I'm not sure what kind of information they want at askubuntu. You can also post in the sticky threads about compatibility in the [Hardware Forum]("http://ubuntuforums.org/forumdisplay.php?f=332")

---

### Post by andfree on 2015-03-23
> **anthonyjeswald said:**
> Well, I just reinstalled 12.04.5, and it's working (and shutting down) perfectly. It must be something in the 14.x kernel.

I just installed 12.04.5 and still have the same problems.

---

### Post by andfree on 2015-03-23
> **sudodus said:**
> Yes, stay with / go back to ***12.04 LTS***, which works for you. But you must select a flavour that is supported. (Lubuntu is long gone. Xubuntu will reach end of life in April this year.)

Standard Ubuntu and Kubuntu will be supported until April 2017. The community re-spins Bento, Bodhi and LXLE also promise support until April 2017. Another light alternative is [Precise Gnome Classic Tweaks]("https://help.ubuntu.com/community/PreciseGnomeClassicTweaks").

**Kubuntu** doesn't install and doesn't get into a live session. I get the message:

```
This kernel requires the following features not present on the CPU: 
pae
Unable to boot - please use a kernel appropriate for your CPU.
```

and forcepae option does nothing.

**Bodhi** doesn't install and doesn't get into a live session. Boot menu page freezes and some black dots appear at the top of it.

**LXLE** doesn't install. When I double-click on the install icon on the live desktop, the cursor spins for a while and stops, and nothing else happens. And shutdown from the live session doesn't work.

**Bento** doesn't install. I get the message:

```
The installer encountered an unrecoverable error. A desktop session will now be run so that you may investigate the problem or try installing again.
```

And the install icon on the live desktop doesn't work. When I double-click on it, the cursor spins for a while and stops, and nothing else happens.

_But shutdown from the live session works._

Only **Torios** and **TahrPup** have been installed and shutdown normally.

---

### Post by kerry_s on 2015-03-23
always install from the live session, the install now, with just the installer does not always work right, at least not for me.

so only the lightest distro versions installed, what are your specs ?

---

### Post by sudodus on 2015-03-23
> **andfree said:**
> **...**
Only **Torios** and **TahrPup** have been installed and shutdown normally.

The following command line makes ***LibreOffice*** work in **ToriOS-beta**. (It is a problem with permissions.)

```
sudo chown -R $USER ~/.config
```

---

### Post by andfree on 2015-03-23
> **kerry_s said:**
> so only the lightest distro versions installed, what are your specs ? 

See [#1]("http://ubuntuforums.org/showthread.php?t=2270322&p=13250173#post13250173") (at the end)

> **sudodus said:**
> The following command line makes ***LibreOffice*** work in **ToriOS-beta**. (It is a problem with permissions.)

```
sudo chown -R $USER ~/.config
```

Thanks a lot.

---

### Post by sudodus on 2015-03-23
> **andfree said:**
> [QUOTE=sudodus;13251077]The following command line makes ***LibreOffice*** work in **ToriOS-beta**. (It is a problem with permissions.)

```
sudo chown -R $USER ~/.config
```

Thanks a lot.[/QUOTE]

You are welcome :-)

---

### Post by kerry_s on 2015-03-23
so your good then, you have a working os ?

no pae & 1gb ram, your lucky to be able to keep that thing going.

---

### Post by andfree on 2015-03-23
> **kerry_s said:**
> so your good then, you have a working os ?

no pae & 1gb ram, your lucky to be able to keep that thing going.

Yeah, after all, I think I am.

---

