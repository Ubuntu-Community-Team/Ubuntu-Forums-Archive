---
title: "&quot;My Passport&quot; problems, cant locate this drive!"
date: 2014-04-12
forum: General Help
---

### Post by tkillby on 2014-04-12
I've recently switched my home computer from xp to ubuntu 14.04. Thank god xp expired and I was able to convince my wife! I've been running ubuntu for several years on old laptops so I'm not totally new but close. I've been researching this issue for several days now with no luck so I'm starting from scratch. 
I got a portable hard drive, my passport, 1 TB, that my daughter never used. I'm currently dual booting WinXP and Ubuntu until I'm confident I have all my documents and photos backed up properly, I was using Mozy but they arent compatible yet with ubuntu so I want to eliminate them. 
I've tried on WinXP, Win7 and Win8 to update the firmware on the passport, it fails everytime, tried several downloads, several methods, so I gave up. On windows it shows up in "devices and printers" but I cant access it to format it or anything. 
Its also not showing up for ubuntu. In my research I tried this command,  ls -l /dev/* | wc -l, before and after plugging in the drive, before it came up with 520 devices, after, 527, this is the only sign I have that Ubuntu even sees this drive, I cant find it anywhere. I'd love to be able to format it and use it, it's maybe 3 years old, never really used, but run out of ideas. 
I'm hoping someone could take me through this and try and locate this drive and force mount it, or whatever. Even if we have to do something in Windows, I'll try anything.
I can post error messages on the terminal, whatever it takes to solve this, thanks all.

---

### Post by steeldriver on 2014-04-12
Well iirc those WD Passport drives have some kind of funny bootable "virtual CD" with a Windows (or Mac) unlocker that autoruns when the drive is inserted - I played with one at one point and wasn't able to mount it from Linux

If you don't want any of the data, it *may* be possible to reformat the whole drive - or that might brick it entirely, I don't know

---

### Post by tkillby on 2014-04-12
thanks for the reply, I've read different things, some say it showed up in Ubuntu just like in Windows, as soon as you plug it in. The issue is it wont pop up in either OS. I know its there, I've seen it in "devices and printers" as well as under the usb drives in ubuntu. I just need someone with the terminal command knowledge to walk me through forcing it to mount.

---

### Post by steeldriver on 2014-04-12
Well instead of just counting the contents of /dev, you could start with the following more specific commands to list the recognized *block devices*

```

sudo blkid -c /dev/null

sudo parted -l

```

Once we see that, it will be easier to figure out how to go about mounting.

---

### Post by tkillby on 2014-04-12
ok, doing a chkdsk on the win7 laptop now, but I'll do that soon, thanks

---

### Post by tkillby on 2014-04-12
Here's what I get

/dev/sda1: UUID="0280615280614CEB" TYPE="ntfs" 
/dev/sda5: UUID="44729a03-12b1-4932-88c6-60f17358e556" TYPE="ext4" 
/dev/sda6: UUID="c159d3b6-f2bb-48e5-a42e-b25d6c44f328" TYPE="swap" 
toby@toby-M68M-S2P:~$ sudo parted -l
Model: ATA WDC WD2500KS-00M (scsi)
Disk /dev/sda: 250GB
Sector size (logical/physical): 512B/512B
Partition Table: msdos


Number  Start   End    Size    Type      File system     Flags
 1      32.3kB  199GB  199GB   primary   ntfs            boot
 2      199GB   250GB  50.9GB  extended
 5      199GB   248GB  48.8GB  logical   ext4
 6      248GB   250GB  2146MB  logical   linux-swap(v1)

---

### Post by steeldriver on 2014-04-13
Well that looks like just your internal disk (dual boot windows / ubuntu?) - I see no evidence of the My Passport drive having been detected as a block device. Does lshw show anything?

```
sudo lshw -C disk
```

Another thing you can try is to monitor the detection process via the system log by typing

```
tail -f /var/log/syslog
```

in a terminal and then plugging the device in / out (type Ctrl-C to exit from the tail process).

---

### Post by tkillby on 2014-04-13
Thanks again for your help, first command;

  *-cdrom:0               
       description: DVD-RAM writer
       product: DVD-RAM GSA-H22N
       vendor: HL-DT-ST
       physical id: 0.0.0
       bus info: scsi@0:0.0.0
       logical name: /dev/cdrom
       logical name: /dev/sr0
       version: 1.00
       serial: [
       capabilities: removable audio cd-r cd-rw dvd dvd-r dvd-ram
       configuration: ansiversion=5 status=nodisc
  *-cdrom:1
       description: SCSI CD-ROM
       physical id: 0.1.0
       bus info: scsi@0:0.1.0
       logical name: /dev/sr1
       capabilities: audio
       configuration: status=nodisc
  *-disk
       description: ATA Disk
       product: WDC WD2500KS-00M
       vendor: Western Digital
       physical id: 0.0.0
       bus info: scsi@2:0.0.0
       logical name: /dev/sda
       version: 02.0
       serial: WD-WCANKA809780
       size: 232GiB (250GB)
       capabilities: partitioned partitioned:dos
       configuration: ansiversion=5 sectorsize=512 signature=00000001
  *-disk
       description: SCSI Disk
       product: My Passport 0740
       vendor: WD
       physical id: 0.0.0
       bus info: scsi@9:0.0.0
       logical name: /dev/sdb
       version: 1003
       serial: WX41A71M8550
       configuration: ansiversion=6 sectorsize=512

---

### Post by tkillby on 2014-04-13
Second command, started unplugged then plugged in, thanks

toby@toby-M68M-S2P:~$ tail -f /var/log/syslog
Apr 13 10:07:12 toby-M68M-S2P AptDaemon.Trans: INFO: Queuing transaction /org/debian/apt/transaction/9248223c040e451fa53c03047d810df4
Apr 13 10:07:12 toby-M68M-S2P AptDaemon.Worker: INFO: Simulating trans: /org/debian/apt/transaction/9248223c040e451fa53c03047d810df4
Apr 13 10:07:13 toby-M68M-S2P AptDaemon.Worker: INFO: Processing transaction /org/debian/apt/transaction/9248223c040e451fa53c03047d810df4
Apr 13 10:07:17 toby-M68M-S2P AptDaemon.Worker: INFO: Updating cache
Apr 13 10:07:19 toby-M68M-S2P AptDaemon.Worker: INFO: Finished transaction /org/debian/apt/transaction/9248223c040e451fa53c03047d810df4
Apr 13 10:12:19 toby-M68M-S2P kernel: [53836.968949] sd 9:0:0:0: timing out command, waited 20s
Apr 13 10:17:01 toby-M68M-S2P CRON[28759]: (root) CMD (   cd / && run-parts --report /etc/cron.hourly)
Apr 13 10:17:44 toby-M68M-S2P AptDaemon: INFO: Quitting due to inactivity
Apr 13 10:17:44 toby-M68M-S2P AptDaemon: INFO: Quitting was requested
Apr 13 10:45:24 toby-M68M-S2P kernel: [55823.689041] usb 1-1: USB disconnect, device number 7
Apr 13 10:45:33 toby-M68M-S2P kernel: [55832.928166] usb 1-1: new high-speed USB device number 8 using ehci-pci
Apr 13 10:45:33 toby-M68M-S2P kernel: [55833.061735] usb 1-1: New USB device found, idVendor=1058, idProduct=0740
Apr 13 10:45:33 toby-M68M-S2P kernel: [55833.061748] usb 1-1: New USB device strings: Mfr=1, Product=2, SerialNumber=5
Apr 13 10:45:33 toby-M68M-S2P kernel: [55833.061756] usb 1-1: Product: My Passport 0740
Apr 13 10:45:33 toby-M68M-S2P kernel: [55833.061762] usb 1-1: Manufacturer: Western Digital
Apr 13 10:45:33 toby-M68M-S2P kernel: [55833.061767] usb 1-1: SerialNumber: 575834314137314D38353530
Apr 13 10:45:33 toby-M68M-S2P kernel: [55833.062703] usb-storage 1-1:1.0: USB Mass Storage device detected
Apr 13 10:45:33 toby-M68M-S2P kernel: [55833.064613] scsi10 : usb-storage 1-1:1.0
Apr 13 10:45:33 toby-M68M-S2P mtp-probe: checking bus 1, device 8: "/sys/devices/pci0000:00/0000:00:02.1/usb1/1-1"
Apr 13 10:45:33 toby-M68M-S2P mtp-probe: bus: 1, device: 8 was not an MTP device
Apr 13 10:45:34 toby-M68M-S2P kernel: [55834.065720] scsi 10:0:0:0: Direct-Access     WD       My Passport 0740 1003 PQ: 0 ANSI: 6
Apr 13 10:45:34 toby-M68M-S2P kernel: [55834.066329] scsi 10:0:0:1: Enclosure         WD       SES Device       1003 PQ: 0 ANSI: 6
Apr 13 10:45:34 toby-M68M-S2P kernel: [55834.067042] sd 10:0:0:0: Attached scsi generic sg3 type 0
Apr 13 10:45:34 toby-M68M-S2P kernel: [55834.067231] ses 10:0:0:1: Attached Enclosure device
Apr 13 10:45:34 toby-M68M-S2P kernel: [55834.067378] ses 10:0:0:1: Attached scsi generic sg4 type 13
Apr 13 10:45:36 toby-M68M-S2P kernel: [55836.042781] usb 1-1: USB disconnect, device number 8
Apr 13 10:45:36 toby-M68M-S2P kernel: [55836.046769] sd 10:0:0:0: [sdb] READ CAPACITY failed
Apr 13 10:45:36 toby-M68M-S2P kernel: [55836.046779] sd 10:0:0:0: [sdb]  
Apr 13 10:45:36 toby-M68M-S2P kernel: [55836.046785] Result: hostbyte=DID_NO_CONNECT driverbyte=DRIVER_OK
Apr 13 10:45:36 toby-M68M-S2P kernel: [55836.046791] sd 10:0:0:0: [sdb] Sense not available.
Apr 13 10:45:36 toby-M68M-S2P kernel: [55836.046852] sd 10:0:0:0: [sdb] Write Protect is off
Apr 13 10:45:36 toby-M68M-S2P kernel: [55836.046867] sd 10:0:0:0: [sdb] Mode Sense: 00 06 04 52
Apr 13 10:45:36 toby-M68M-S2P kernel: [55836.046957] sd 10:0:0:0: [sdb] No Caching mode page found
Apr 13 10:45:36 toby-M68M-S2P kernel: [55836.046968] sd 10:0:0:0: [sdb] Assuming drive cache: write through
Apr 13 10:45:36 toby-M68M-S2P kernel: [55836.047398] sd 10:0:0:0: [sdb] READ CAPACITY failed
Apr 13 10:45:36 toby-M68M-S2P kernel: [55836.047405] sd 10:0:0:0: [sdb]  
Apr 13 10:45:36 toby-M68M-S2P kernel: [55836.047409] Result: hostbyte=DID_NO_CONNECT driverbyte=DRIVER_OK
Apr 13 10:45:36 toby-M68M-S2P kernel: [55836.047414] sd 10:0:0:0: [sdb] Sense not available.
Apr 13 10:45:36 toby-M68M-S2P kernel: [55836.047455] sd 10:0:0:0: [sdb] Asking for cache data failed
Apr 13 10:45:36 toby-M68M-S2P kernel: [55836.047460] sd 10:0:0:0: [sdb] Assuming drive cache: write through
Apr 13 10:45:36 toby-M68M-S2P kernel: [55836.047467] sd 10:0:0:0: [sdb] Attached SCSI disk
Apr 13 10:45:36 toby-M68M-S2P kernel: [55836.054210] ses 10:0:0:1: Failed to get diagnostic page 0x10000
Apr 13 10:45:36 toby-M68M-S2P kernel: [55836.054224] ses 10:0:0:1: Failed to bind enclosure -19
^C

---

### Post by tkillby on 2014-04-14
No one?

---

