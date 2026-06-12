---
title: "External CDDVDW not working correctly"
date: 2013-05-28
forum: General Help
---

### Post by asensio on 2013-05-28
Hi,

I have a problem with an external Samsung SE-S204N DVD writer drive. Thinking it could be a Hardware problem I posted [some questions]("http://ubuntuforums.org/showthread.php?t=2148323") at the "Hardware Forum" but no one could help.

I've been exploring other ways. Since the drive works on a win machine, I'm thinking it not hardware but a problem in Ubuntu (I'm using Ubuntu LTS 12.04.2 x64, and this is a fresh install)
Adding to the "tests" I did, and posted on the link above, I looked at my fstab. Here is the line for the external DVD-RW:

```
/dev/sr1        /media/floppy0  auto   rw,user,noauto,exec,utf8 0       0
```

Could this line be the problem? Searching a little more on the web, I saw that some fstab for DVD-RW had a "udf,iso9660" or where read only (ro) instead of Read-Write (rw)
Hope someone can help.
Thanks.
Cheers,
**ASENSIO **

---

### Post by asensio on 2013-05-29
anyone? someone?
:(
**asensio**

---

### Post by mc4man on 2013-05-29
Post the *-cdrom section of this with the drive **connected after booting up**
```
sudo lshw -C disk
```

Unless you have some specific need for an fstab entry  on the drive then just remove the entry or comment out & reboot
(put a # in front of, like
```
#/dev/sr1        /media/floppy0  auto   rw,user,noauto,exec,utf8 0       0
```

---

### Post by asensio on 2013-05-29
Thanks for your reply, mc4man

I commented out the line in fstab, as you said, and here's the output of **:~$ sudo lshw -C disk** right after boot.

```
*-cdrom UNCLAIMED
       descrição: SCSI CD-ROM
       physical id: 0.0.0
       informações do barramento: scsi@4:0.0.0
```


just to see the difference, [COLOR="#FF0000"]before I edited the fstab[/COLOR] the output was this:

```
*-cdrom
       descrição: DVD-RAM writer
       produto: CDDVDW SE-S204N
       fabricante: TSSTcorp
       physical id: 0.0.0
       informações do barramento: scsi@4:0.0.0
       nome lógico: /dev/cdrom
       nome lógico: /dev/sr1
       versão: TS00
       capabilities: removable audio cd-r cd-rw dvd dvd-r dvd-ram
       configuração: status=ready
     *-medium
          physical id: 0
          nome lógico: /dev/cdrom
```


I never had problems with this drive, and i've been using Ubuntu for some years now, so the first thing I thought was it must be an hardware fault. But now it doesn't look it is.
Hope you can help and again, thank you.
Cheers.

---

### Post by mc4man on 2013-05-30
don't know why you're getting an unclaimed, in 12.04 the drive should be recognized & assigned the next available /dev*, typically sr1 & when inserting media with a filesystem mounted to /media/<volume label of inserted media>
ex. here on 12.04 with an ext. drive connected & dvd inserted
> *-cdrom
       description: DVD reader
       product: DVD/HD  X807616
       vendor: TOSHIBA
       physical id: 0.0.0
       bus info: scsi@7:0.0.0
       logical name: /dev/cdrom1
       logical name: /dev/dvd1
       logical name: /dev/sr1
       logical name: /media/LASTWALTZ
       version: MC08
       capabilities: removable audio dvd
       configuration: mount.fstype=udf mount.options=ro,nosuid,nodev,relatime,uid=1000,gid=1000,umask=77,dmode=500,iocharset=utf8 state=mounted status=ready


You could post the contents of this file in a code box, maybe something of interest
/etc/udev/rules.d/70-persistent-cd.rules

Also  with drive connected does it show in this command
```
ls -la /dev/disk/by-id
```

If wanting to use an fstab try like this - (red matching what was reported as assigned link from above command
```
sudo mkdir /media/cdrom1
```
```
/dev/sr[COLOR="#FF0000"]1[/COLOR]   /media/cdrom1   udf,iso9660 user,noauto,exec   0 0
```

---

### Post by asensio on 2013-05-30
Hi and thanks for your help

the **70-persistent-cd.rules** file content (note that I also have an old internal DVD reader):
```
# This file maintains persistent names for CD/DVD reader and writer devices.
# See udev(7) for syntax.
#
# Entries are automatically added by the 75-cd-aliases-generator.rules
# file; however you are also free to add your own entries provided you
# add the ENV{GENERATED}=1 flag to your own rules as well.
# USB_Mass_Storage_Device (pci-0000:00:1d.7-usb-0:3:1.0-scsi-0:0:0:0)
SUBSYSTEM=="block", ENV{ID_CDROM}=="?*", ENV{ID_SERIAL}=="TSSTcorp_USB_Mass_Storage_Device_SATAHH0000000001570", SYMLINK+="cdrom", ENV{GENERATED}="1"

#  (pci-0000:00:1f.1-scsi-0:0:1:0)
SUBSYSTEM=="block", ENV{ID_CDROM}=="?*", ENV{ID_PATH}=="pci-0000:00:1f.1-scsi-0:0:1:0", SYMLINK+="cdrom1", ENV{GENERATED}="1"
SUBSYSTEM=="block", ENV{ID_CDROM}=="?*", ENV{ID_PATH}=="pci-0000:00:1f.1-scsi-0:0:1:0", SYMLINK+="dvd1", ENV{GENERATED}="1"
```


**ls -la /dev/disk/by-id** shows the drive:
```
lrwxrwxrwx 1 root root   9 Mai 30 13:52 usb-TSSTcorp_USB_Mass_Storage_Device_SATAHH0000000001570 -> ../../sr1
```

Oddly it always mounted in /media/floppy... I'll try **mkdir /media/cdrom** since cdrom1 seems to be linked to the other drive. 
I'll edit this post something changes.

**EDIT:** Still nothing. Now I have the "cdrom" shortcut in Nautilus but, when I click it, I get a * mount: /dev/sr1 already montaded or /media/cdrom busy* window.
Right-clicking and choosing "mount" I get *DBus error org.gtk.Private.RemoteVolumeMonitor.Failed: An operation is already pending*

Thank you,
Cheers

---

### Post by asensio on 2013-06-02
Hi,

It seems the problem is not the drive itself, I think it must be something with the USB mounting. Ubuntu/Nautilus I can't mount any usb flash drive. The only way I can do the mounting is from palimpsest, but the reading/writing speed is too slow, even intermitent. I have another Ubuntu Precised pc that has no problem with this two drives...

Here's **dmesg** of an MP3 player/SD card reader

```
[ 5900.428028] usb 1-3: new high-speed USB device number 8 using ehci_hcd
[ 5900.608201] usb 1-3: device descriptor read/all, error -71
[ 5900.724033] usb 1-3: new high-speed USB device number 9 using ehci_hcd
[ 5900.865448] usb 1-3: New USB device found, idVendor=0d7d, idProduct=1651
[ 5900.865456] usb 1-3: New USB device strings: Mfr=1, Product=2, SerialNumber=0
[ 5900.865461] usb 1-3: Product: CARD MP3 20X
[ 5900.865465] usb 1-3: Manufacturer:  
[ 5900.866355] scsi8 : usb-storage 1-3:1.0
[ 5901.792061] sr 4:0:0:0: rejecting I/O to offline device
[ 5901.865101] scsi 8:0:0:0: Direct-Access              CARD MP3 20X     1.03 PQ: 0 ANSI: 0 CCS
[ 5901.865958] sd 8:0:0:0: Attached scsi generic sg4 type 0
[ 5901.869605] sd 8:0:0:0: [sdc] Attached SCSI removable disk
[ 5903.840047] sr 4:0:0:0: rejecting I/O to offline device
[ 5905.888042] sr 4:0:0:0: rejecting I/O to offline device
[ 5907.936042] sr 4:0:0:0: rejecting I/O to offline device
[ 5909.984043] sr 4:0:0:0: rejecting I/O to offline device
[ 5912.032047] sr 4:0:0:0: rejecting I/O to offline device
[ 5912.094365] sr 4:0:0:0: rejecting I/O to offline device
[ 5912.094388] sr 4:0:0:0: rejecting I/O to offline device
[ 5912.094399] sr 4:0:0:0: rejecting I/O to offline device
[ 5914.592046] sr 4:0:0:0: rejecting I/O to offline device
[ 5916.640076] sr 4:0:0:0: rejecting I/O to offline device
[ 5918.688041] sr 4:0:0:0: rejecting I/O to offline device
[ 5920.736050] sr 4:0:0:0: rejecting I/O to offline device
[ 5922.784046] sr 4:0:0:0: rejecting I/O to offline device
[ 5924.832049] sr 4:0:0:0: rejecting I/O to offline device
[ 5926.880041] sr 4:0:0:0: rejecting I/O to offline device
[ 5928.928044] sr 4:0:0:0: rejecting I/O to offline device
[ 5930.976046] sr 4:0:0:0: rejecting I/O to offline device
[ 5933.024040] sr 4:0:0:0: rejecting I/O to offline device
[ 5935.072053] sr 4:0:0:0: rejecting I/O to offline device
[ 5937.120031] sr 4:0:0:0: rejecting I/O to offline device
[ 5937.872243] usb 1-3: USB disconnect, device number 9
[ 5939.168042] sr 4:0:0:0: rejecting I/O to offline device
[ 5939.748026] usb 1-3: new high-speed USB device number 10 using ehci_hcd
[ 5939.889581] usb 1-3: New USB device found, idVendor=0d7d, idProduct=1651
[ 5939.889589] usb 1-3: New USB device strings: Mfr=1, Product=2, SerialNumber=0
[ 5939.889594] usb 1-3: Product: CARD MP3 20X
[ 5939.889599] usb 1-3: Manufacturer:  
[ 5939.890464] scsi9 : usb-storage 1-3:1.0
```

I'm out of ideas. It would be great to have some help, since this is a recent instalation and I'm only going to reinstall if there's no alternative.
Cheers.

---

### Post by asensio on 2013-07-07
I've been googling for some time now, no luck in finding an answer. But I haven't tried to plug a USB flash drive since I wrote the first post of this thread. I tried it now and I could not get it to work. Got my hands on a laptop with ubuntu and tried the same DVDRW and flash drive and they both worked... I tried to see what was the difference between both systems with some commands:

```
**lsmod | grep -i usb**

**[COLOR="#008000"]->Working (laptop)[/COLOR]**
[    0.246559] usbcore: registered new interface driver usbfs
[    0.246577] usbcore: registered new interface driver hub
[    0.246619] usbcore: registered new device driver usb
[    0.962340] ehci_hcd: USB 2.0 'Enhanced' Host Controller (EHCI) Driver
[    0.962462] ehci_hcd 0000:00:1d.7: new USB bus registered, assigned bus number 1
[    0.980022] ehci_hcd 0000:00:1d.7: USB 2.0 started, EHCI 1.00
[    0.980213] hub 1-0:1.0: USB hub found
[    0.980344] ohci_hcd: USB 1.1 'Open' Host Controller (OHCI) Driver
[    0.980365] uhci_hcd: USB Universal Host Controller Interface driver
[    0.980471] uhci_hcd 0000:00:1d.0: new USB bus registered, assigned bus number 2
[    0.980705] hub 2-0:1.0: USB hub found
[    0.980894] uhci_hcd 0000:00:1d.1: new USB bus registered, assigned bus number 3
[    0.981121] hub 3-0:1.0: USB hub found
[    0.981303] uhci_hcd 0000:00:1d.2: new USB bus registered, assigned bus number 4
[    0.981533] hub 4-0:1.0: USB hub found
[    0.981714] uhci_hcd 0000:00:1d.3: new USB bus registered, assigned bus number 5
[    0.981950] hub 5-0:1.0: USB hub found
[    0.982121] usbcore: registered new interface driver libusual
[   53.732059] usb 1-5: new high-speed USB device number 2 using ehci_hcd
[   53.908228] Initializing USB Mass Storage driver...
[   53.918468] scsi2 : usb-storage 1-5:1.0
[   53.918627] usbcore: registered new interface driver usb-storage
[   53.918631] USB Mass Storage support registered.
[   54.917130] scsi 2:0:0:0: Direct-Access              USB DISK 2.0     PMAP PQ: 0 ANSI: 0 CCS
[  235.003391] usb 1-5: USB disconnect, device number 2
[  238.032214] usb 1-5: new high-speed USB device number 3 using ehci_hcd
[  238.169849] scsi3 : usb-storage 1-5:1.0
[  239.169236] scsi 3:0:0:0: Direct-Access              USB DISK 2.0     PMAP PQ: 0 ANSI: 0 CCS
[  403.314784] usb 1-5: USB disconnect, device number 3
[  407.460196] usb 1-5: new high-speed USB device number 4 using ehci_hcd
[  407.597647] scsi4 : usb-storage 1-5:1.0
[  408.597183] scsi 4:0:0:0: Direct-Access              USB DISK 2.0     PMAP PQ: 0 ANSI: 0 CCS

[COLOR="#FF0000"]->Not Working (desktop)[/COLOR]
[  847.172032] usb 1-3: new high-speed USB device number 10 using ehci_hcd
[  847.308390] usb 1-3: New USB device found, idVendor=13fe, idProduct=1a00
[  847.308398] usb 1-3: New USB device strings: Mfr=1, Product=2, SerialNumber=3
[  847.308403] usb 1-3: Product: USB DISK 2.0    
[  847.308407] usb 1-3: Manufacturer:         
[  847.308412] usb 1-3: SerialNumber: 077B11A0056D
[  847.309148] scsi9 : usb-storage 1-3:1.0
[  848.309662] scsi 9:0:0:0: Direct-Access              USB DISK 2.0     PMAP PQ: 0 ANSI: 0 CCS
[  848.436031] usb 1-3: reset high-speed USB device number 10 using ehci_hcd
[  848.708037] usb 1-3: reset high-speed USB device number 10 using ehci_hcd
[  848.976036] usb 1-3: reset high-speed USB device number 10 using ehci_hcd
[  849.248045] usb 1-3: reset high-speed USB device number 10 using ehci_hcd
```


```
**tail -f /var/log/syslog**

**[COLOR="#008000"]->Working[/COLOR]**
Jul  7 04:54:44 Laptop kernel: [ 1686.504187] usb 1-5: new high-speed USB device number 6 using ehci_hcd
Jul  7 04:54:44 Laptop kernel: [ 1686.642084] scsi6 : usb-storage 1-5:1.0
Jul  7 04:54:44 Laptop mtp-probe: checking bus 1, device 6: "/sys/devices/pci0000:00/0000:00:1d.7/usb1/1-5"
Jul  7 04:54:44 Laptop mtp-probe: bus: 1, device: 6 was not an MTP device
Jul  7 04:54:45 Laptop kernel: [ 1687.640924] scsi 6:0:0:0: Direct-Access              USB DISK 2.0     PMAP PQ: 0 ANSI: 0 CCS
Jul  7 04:54:45 Laptop kernel: [ 1687.642616] sd 6:0:0:0: Attached scsi generic sg2 type 0
Jul  7 04:54:45 Laptop kernel: [ 1687.874488] sd 6:0:0:0: [sdb] 8060928 512-byte logical blocks: (4.12 GB/3.84 GiB)
Jul  7 04:54:45 Laptop kernel: [ 1687.875162] sd 6:0:0:0: [sdb] Write Protect is off
Jul  7 04:54:45 Laptop kernel: [ 1687.875171] sd 6:0:0:0: [sdb] Mode Sense: 23 00 00 00
Jul  7 04:54:45 Laptop kernel: [ 1687.875773] sd 6:0:0:0: [sdb] No Caching mode page present
Jul  7 04:54:45 Laptop kernel: [ 1687.875781] sd 6:0:0:0: [sdb] Assuming drive cache: write through
Jul  7 04:54:45 Laptop kernel: [ 1687.880292] sd 6:0:0:0: [sdb] No Caching mode page present
Jul  7 04:54:45 Laptop kernel: [ 1687.880301] sd 6:0:0:0: [sdb] Assuming drive cache: write through
Jul  7 04:54:45 Laptop kernel: [ 1687.881263]  sdb: sdb1
Jul  7 04:54:45 Laptop kernel: [ 1687.886744] sd 6:0:0:0: [sdb] No Caching mode page present
Jul  7 04:54:45 Laptop kernel: [ 1687.886752] sd 6:0:0:0: [sdb] Assuming drive cache: write through
Jul  7 04:54:45 Laptop kernel: [ 1687.886759] sd 6:0:0:0: [sdb] Attached SCSI removable disk
Jul  7 04:54:47 Laptop kernel: [ 1689.212244] EXT4-fs (sdb1): mounted filesystem with ordered data mode. Opts: (null)

[COLOR="#FF0000"]->Not Working[/COLOR]
Jul  7 04:52:28 Linux kernel: [ 1606.008033] usb 1-3: new high-speed USB device number 14 using ehci_hcd
Jul  7 04:52:28 Linux kernel: [ 1606.153289] usb 1-3: New USB device found, idVendor=13fe, idProduct=1a00
Jul  7 04:52:28 Linux kernel: [ 1606.153297] usb 1-3: New USB device strings: Mfr=1, Product=2, SerialNumber=3
Jul  7 04:52:28 Linux kernel: [ 1606.153302] usb 1-3: Product: USB DISK 2.0    
Jul  7 04:52:28 Linux kernel: [ 1606.153307] usb 1-3: Manufacturer:         
Jul  7 04:52:28 Linux kernel: [ 1606.153311] usb 1-3: SerialNumber: 077B11A0056D
Jul  7 04:52:28 Linux kernel: [ 1606.153916] scsi12 : usb-storage 1-3:1.0
Jul  7 04:52:28 Linux mtp-probe: checking bus 1, device 14: "/sys/devices/pci0000:00/0000:00:1d.7/usb1/1-3"
Jul  7 04:52:28 Linux mtp-probe: bus: 1, device: 14 was not an MTP device
Jul  7 04:52:29 Linux kernel: [ 1607.136053] sr 4:0:0:0: rejecting I/O to offline device
Jul  7 04:52:29 Linux kernel: [ 1607.153688] scsi 12:0:0:0: Direct-Access              USB DISK 2.0     PMAP PQ: 0 ANSI: 0 CCS
Jul  7 04:52:29 Linux kernel: [ 1607.154597] sd 12:0:0:0: Attached scsi generic sg4 type 0
Jul  7 04:52:29 Linux kernel: [ 1607.388054] usb 1-3: reset high-speed USB device number 14 using ehci_hcd
Jul  7 04:52:30 Linux kernel: [ 1607.537303] sd 12:0:0:0: [sdc] 8060928 512-byte logical blocks: (4.12 GB/3.84 GiB)
Jul  7 04:52:30 Linux kernel: [ 1607.537791] sd 12:0:0:0: [sdc] Write Protect is off
Jul  7 04:52:30 Linux kernel: [ 1607.537797] sd 12:0:0:0: [sdc] Mode Sense: 23 00 00 00
Jul  7 04:52:30 Linux kernel: [ 1607.538291] sd 12:0:0:0: [sdc] No Caching mode page present
Jul  7 04:52:30 Linux kernel: [ 1607.538297] sd 12:0:0:0: [sdc] Assuming drive cache: write through
Jul  7 04:52:30 Linux kernel: [ 1607.541669] sd 12:0:0:0: [sdc] No Caching mode page present
Jul  7 04:52:30 Linux kernel: [ 1607.541677] sd 12:0:0:0: [sdc] Assuming drive cache: write through
Jul  7 04:52:30 Linux kernel: [ 1607.542434]  sdc: sdc1
Jul  7 04:52:30 Linux kernel: [ 1607.545994] sd 12:0:0:0: [sdc] No Caching mode page present
Jul  7 04:52:30 Linux kernel: [ 1607.546004] sd 12:0:0:0: [sdc] Assuming drive cache: write through
Jul  7 04:52:30 Linux kernel: [ 1607.546011] sd 12:0:0:0: [sdc] Attached SCSI removable disk
Jul  7 04:52:30 Linux kernel: [ 1607.760061] usb 1-3: reset high-speed USB device number 14 using ehci_hcd
```


```
**lspci | grep -i ehci**

**[COLOR="#008000"]->Working[/COLOR]**
00:1d.7 USB controller: Intel Corporation N10/ICH 7 Family USB2 EHCI Controller (rev 02) **<-- (?)**

[COLOR="#FF0000"]->Not Working[/COLOR]
00:1d.7 USB controller: Intel Corporation N10/ICH 7 Family USB2 EHCI Controller (rev 01) **<-- (?)**
```


```
**uname -a** 

**[COLOR="#008000"]->Working[/COLOR]**
Linux Laptop 3.2.0-50-generic-pae #76~pre201306210400-Ubuntu SMP Fri Jun 21 09:15:26 UTC 2013 i686 i686 i386 GNU/Linux **<-- (32bit)**

[COLOR="#FF0000"]->Not Working[/COLOR]
Linux Linux 3.5.0-36-generic #57~precise1-Ubuntu SMP Thu Jun 20 18:21:09 UTC 2013 x86_64 x86_64 x86_64 GNU/Linux **<-- (64bit)**
```

When I was searching around I came across several users that seem to have trouble with USB devices under Ubuntu 64bit, seems this is also my case... I never used a 64bit version of Ubuntu before and all devices worked until now.
If someone has a better explanation please share :)
Thank you very much.
Cheers.

---

