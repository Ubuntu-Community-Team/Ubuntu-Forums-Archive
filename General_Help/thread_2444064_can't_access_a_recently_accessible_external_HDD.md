---
title: "can't access a recently accessible external HDD"
date: 2020-05-24
forum: General Help
---

### Post by pjstock on 2020-05-24
I've never NOT received a helpful reply to a question I've posted in the Forum. But the one I posted about a week ago under Hardware hasn't generated any interest or help.
Maybe (even though it related to a Harddrive) it's not really about hardware (as it was about access and permissions, which is software really.)
so, I am going to repoost this under General Help. I hope reposting doesn't violate any rules- but I couldn't figure out how to move the posting or to delete the one under Hardware.

for years I've used a 2TB seagate external USB harddrive as my primary storage.

8 weeks ago I disconnected it (i believe while my desktop system was OFF) from my Desktop #1 and took it to a remote location where i plugged it into Desktop #2. It functioned perfectly.
both systems are running Ubuntu 18.04.4 LTS.

yesterday I returned to DT #1, plugged in the Seagate HDD, booted up as usual,
but am getting an error "Unable to Acess....." " Not Authorized to Perform Operation".

it appears the troublesome Seagate HDD is not mounting. Nor am I able to "Mount" it manually.

I then plugged the HDD into a laptop (also running Ubuntu 18.04.4 ) and it worked fine.

so what could have happened to my Desktop #1 during my absence that the HDD is not accessible?

Peter

---

### Post by HermanAB on 2020-05-24
I cannot give you an easy recipe to fix it, because the problem is system specific.

The GUI isn't going to help you, since it hides the error messages.

So, unplug it, open a terminal, look at the kernel messages with *dmsg*, plug it in and again look at the kernel messages with *dmsg*.

Look at */etc/fstab* and fix the disk mount line in there (if any), based on what you discovered above.

There may also be a hanging broken mount, which you may need to find with *mount* or *df* and remove with a lazy unmount *umount -l*.

Once you find an error message, copy and paste it into Google, put the word *linux* in front of it and see what comes up.

---

### Post by pjstock on 2020-05-28
thank you.
I am back at this desk after an absence.
(Did you mean DMESG? i expect so.)
that seems to generate a LOT of output. Can you point me to what key bits I should be looking for? I don't expect you would want me to post it all here.

---

### Post by pjstock on 2020-05-28
I pushed the output of the dmesg before and after plugging in the HDD.
I then compared the output text files.
the only difference seems to be this section, at the very end of the file:

```
[14970.539614] usb 2-1.8: new high-speed USB device number 6 using ehci-pci
[14970.694039] usb 2-1.8: New USB device found, idVendor=0bc2, idProduct=3321
[14970.694043] usb 2-1.8: New USB device strings: Mfr=2, Product=3, SerialNumber=1
[14970.694045] usb 2-1.8: Product: Expansion Desk
[14970.694047] usb 2-1.8: Manufacturer: Seagate
[14970.694048] usb 2-1.8: SerialNumber: NA4N2NMT
[14971.074750] usbcore: registered new interface driver usb-storage
[14971.094113] scsi host6: uas
[14971.094229] usbcore: registered new interface driver uas
[14971.095311] scsi 6:0:0:0: Direct-Access     Seagate  Expansion Desk   0604 PQ: 0 ANSI: 6
[14971.097096] sd 6:0:0:0: Attached scsi generic sg2 type 0
[14971.097487] sd 6:0:0:0: [sdb] Spinning up disk...
[14972.119592] .
[14973.143564] .
[14974.167543] .
[14975.191530] .
[14976.215511] .
[14977.239490] .
[14978.263478] .
[14979.287460] .
[14980.311406] .
[14980.311562] ready
[14980.312795] sd 6:0:0:0: [sdb] 488378645 4096-byte logical blocks: (2.00 TB/1.82 TiB)
[14980.312796] sd 6:0:0:0: [sdb] 16384-byte physical blocks
[14980.317044] sd 6:0:0:0: [sdb] Write Protect is off
[14980.317046] sd 6:0:0:0: [sdb] Mode Sense: 4f 00 00 00
[14980.317543] sd 6:0:0:0: [sdb] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[14980.317918] sd 6:0:0:0: [sdb] Optimal transfer size 268431360 bytes not a multiple of physical block size (16384 bytes)
[14980.340500]  sdb: sdb1
[14980.343294] sd 6:0:0:0: [sdb] Attached SCSI disk
```

does that help at all?

---

### Post by pjstock on 2020-05-28
fstab shows:
```
# /etc/fstab: static file system information.
#
# Use 'blkid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
# / was on /dev/sda3 during installation
UUID=73c6a17a-7705-4f71-bdd4-804fef93edd3 /               ext4    errors=remount-ro 0       1
# /home was on /dev/sda4 during installation
UUID=427bb13e-0609-4207-9628-10860c5d6586 /home           ext4    defaults        0       2
/swapfile                                 none            swap    sw              0       0

```

does this show that this HDD ("Seagate") is not mounted.?
because in the GUI it does not seem to be mounteda and I cannot make it mount.

---

### Post by dino99 on 2020-05-28
As you says 'external hdd' then i suppose you plug it via usb ; so do plug it, then glance at 'journalctl -b | grep usb'  from a terminal

---

### Post by pjstock on 2020-05-28
and I get:
```

journalctl -b | grep usb

May 28 11:09:11 peter-OptiPlex-990 kernel: usbcore: registered new interface driver usbfs
May 28 11:09:11 peter-OptiPlex-990 kernel: usbcore: registered new interface driver hub
May 28 11:09:11 peter-OptiPlex-990 kernel: usbcore: registered new device driver usb
May 28 11:09:11 peter-OptiPlex-990 kernel: usb usb1: New USB device found, idVendor=1d6b, idProduct=0002
May 28 11:09:11 peter-OptiPlex-990 kernel: usb usb1: New USB device strings: Mfr=3, Product=2, SerialNumber=1
May 28 11:09:11 peter-OptiPlex-990 kernel: usb usb1: Product: EHCI Host Controller
May 28 11:09:11 peter-OptiPlex-990 kernel: usb usb1: Manufacturer: Linux 4.15.0-99-generic ehci_hcd
May 28 11:09:11 peter-OptiPlex-990 kernel: usb usb1: SerialNumber: 0000:00:1a.0
May 28 11:09:11 peter-OptiPlex-990 kernel: usb usb2: New USB device found, idVendor=1d6b, idProduct=0002
May 28 11:09:11 peter-OptiPlex-990 kernel: usb usb2: New USB device strings: Mfr=3, Product=2, SerialNumber=1
May 28 11:09:11 peter-OptiPlex-990 kernel: usb usb2: Product: EHCI Host Controller
May 28 11:09:11 peter-OptiPlex-990 kernel: usb usb2: Manufacturer: Linux 4.15.0-99-generic ehci_hcd
May 28 11:09:11 peter-OptiPlex-990 kernel: usb usb2: SerialNumber: 0000:00:1d.0
May 28 11:09:11 peter-OptiPlex-990 kernel: usb 1-1: new high-speed USB device number 2 using ehci-pci
May 28 11:09:11 peter-OptiPlex-990 kernel: usb 2-1: new high-speed USB device number 2 using ehci-pci
May 28 11:09:11 peter-OptiPlex-990 kernel: usb 1-1: New USB device found, idVendor=8087, idProduct=0024
May 28 11:09:11 peter-OptiPlex-990 kernel: usb 1-1: New USB device strings: Mfr=0, Product=0, SerialNumber=0
May 28 11:09:11 peter-OptiPlex-990 kernel: usb 2-1: New USB device found, idVendor=8087, idProduct=0024
May 28 11:09:11 peter-OptiPlex-990 kernel: usb 2-1: New USB device strings: Mfr=0, Product=0, SerialNumber=0
May 28 11:09:11 peter-OptiPlex-990 kernel: usb 1-1.4: new high-speed USB device number 3 using ehci-pci
May 28 11:09:11 peter-OptiPlex-990 kernel: usb 2-1.1: new low-speed USB device number 3 using ehci-pci
May 28 11:09:11 peter-OptiPlex-990 kernel: usb 1-1.4: New USB device found, idVendor=04a9, idProduct=221c
May 28 11:09:11 peter-OptiPlex-990 kernel: usb 1-1.4: New USB device strings: Mfr=1, Product=2, SerialNumber=0
May 28 11:09:11 peter-OptiPlex-990 kernel: usb 1-1.4: Product: CanoScan
May 28 11:09:11 peter-OptiPlex-990 kernel: usb 1-1.4: Manufacturer: Canon
May 28 11:09:11 peter-OptiPlex-990 kernel: usb 2-1.1: New USB device found, idVendor=0d62, idProduct=001c
May 28 11:09:11 peter-OptiPlex-990 kernel: usb 2-1.1: New USB device strings: Mfr=1, Product=2, SerialNumber=0
May 28 11:09:11 peter-OptiPlex-990 kernel: usb 2-1.1: Product: USB Combo Keyboard
May 28 11:09:11 peter-OptiPlex-990 kernel: usb 2-1.1: Manufacturer: Darfon
May 28 11:09:11 peter-OptiPlex-990 kernel: usbcore: registered new interface driver usbhid
May 28 11:09:11 peter-OptiPlex-990 kernel: usbhid: USB HID core driver
May 28 11:09:11 peter-OptiPlex-990 kernel: input: Darfon USB Combo Keyboard as /devices/pci0000:00/0000:00:1d.0/usb2/2-1/2-1.1/2-1.1:1.0/0003:0D62:001C.0001/input/input5
May 28 11:09:11 peter-OptiPlex-990 kernel: hid-generic 0003:0D62:001C.0001: input,hidraw0: USB HID v1.00 Keyboard [Darfon USB Combo Keyboard] on usb-0000:00:1d.0-1.1/input0
May 28 11:09:11 peter-OptiPlex-990 kernel: input: Darfon USB Combo Keyboard as /devices/pci0000:00/0000:00:1d.0/usb2/2-1/2-1.1/2-1.1:1.1/0003:0D62:001C.0002/input/input6
May 28 11:09:11 peter-OptiPlex-990 kernel: usb 2-1.2: new full-speed USB device number 4 using ehci-pci
May 28 11:09:11 peter-OptiPlex-990 kernel: hid-generic 0003:0D62:001C.0002: input,hiddev0,hidraw1: USB HID v1.00 Device [Darfon USB Combo Keyboard] on usb-0000:00:1d.0-1.1/input1
May 28 11:09:11 peter-OptiPlex-990 kernel: usb 2-1.2: New USB device found, idVendor=0451, idProduct=2046
May 28 11:09:11 peter-OptiPlex-990 kernel: usb 2-1.2: New USB device strings: Mfr=0, Product=0, SerialNumber=0
May 28 11:09:11 peter-OptiPlex-990 kernel: usb 2-1.6: new low-speed USB device number 5 using ehci-pci
May 28 11:09:11 peter-OptiPlex-990 kernel: usb 2-1.6: New USB device found, idVendor=046d, idProduct=c016
May 28 11:09:11 peter-OptiPlex-990 kernel: usb 2-1.6: New USB device strings: Mfr=1, Product=2, SerialNumber=0
May 28 11:09:11 peter-OptiPlex-990 kernel: usb 2-1.6: Product: Optical USB Mouse
May 28 11:09:11 peter-OptiPlex-990 kernel: usb 2-1.6: Manufacturer: Logitech
May 28 11:09:11 peter-OptiPlex-990 kernel: input: Logitech Optical USB Mouse as /devices/pci0000:00/0000:00:1d.0/usb2/2-1/2-1.6/2-1.6:1.0/0003:046D:C016.0003/input/input7
May 28 11:09:11 peter-OptiPlex-990 kernel: hid-generic 0003:046D:C016.0003: input,hidraw2: USB HID v1.10 Mouse [Logitech Optical USB Mouse] on usb-0000:00:1d.0-1.6/input0
May 28 11:09:22 peter-OptiPlex-990 mtp-probe[388]: checking bus 2, device 5: "/sys/devices/pci0000:00/0000:00:1d.0/usb2/2-1/2-1.6"
May 28 11:09:22 peter-OptiPlex-990 mtp-probe[387]: checking bus 2, device 3: "/sys/devices/pci0000:00/0000:00:1d.0/usb2/2-1/2-1.1"
May 28 11:09:30 peter-OptiPlex-990 audit[883]: AVC apparmor="STATUS" operation="profile_load" profile="unconfined" name="/usr/sbin/ippusbxd" pid=883 comm="apparmor_parser"
May 28 11:09:30 peter-OptiPlex-990 kernel: audit: type=1400 audit(1590678570.040:8): apparmor="STATUS" operation="profile_load" profile="unconfined" name="/usr/sbin/ippusbxd" pid=883 comm="apparmor_parser"
May 28 11:09:45 peter-OptiPlex-990 /usr/lib/gdm3/gdm-x-session[1223]: (**) Option "config_info" "udev:/sys/devices/pci0000:00/0000:00:1d.0/usb2/2-1/2-1.1/2-1.1:1.0/0003:0D62:001C.0001/input/input5/event2"
May 28 11:09:45 peter-OptiPlex-990 /usr/lib/gdm3/gdm-x-session[1223]: (**) Option "config_info" "udev:/sys/devices/pci0000:00/0000:00:1d.0/usb2/2-1/2-1.1/2-1.1:1.1/0003:0D62:001C.0002/input/input6/event3"
May 28 11:09:45 peter-OptiPlex-990 /usr/lib/gdm3/gdm-x-session[1223]: (**) Option "config_info" "udev:/sys/devices/pci0000:00/0000:00:1d.0/usb2/2-1/2-1.6/2-1.6:1.0/0003:046D:C016.0003/input/input7/event4"
May 28 15:18:29 peter-OptiPlex-990 kernel: usb 2-1.8: new high-speed USB device number 6 using ehci-pci
May 28 15:18:29 peter-OptiPlex-990 kernel: usb 2-1.8: New USB device found, idVendor=0bc2, idProduct=3321
May 28 15:18:29 peter-OptiPlex-990 kernel: usb 2-1.8: New USB device strings: Mfr=2, Product=3, SerialNumber=1
May 28 15:18:29 peter-OptiPlex-990 kernel: usb 2-1.8: Product: Expansion Desk
May 28 15:18:29 peter-OptiPlex-990 kernel: usb 2-1.8: Manufacturer: Seagate
May 28 15:18:29 peter-OptiPlex-990 kernel: usb 2-1.8: SerialNumber: NA4N2NMT
May 28 15:18:29 peter-OptiPlex-990 mtp-probe[20105]: checking bus 2, device 6: "/sys/devices/pci0000:00/0000:00:1d.0/usb2/2-1/2-1.8"
May 28 15:18:29 peter-OptiPlex-990 kernel: usbcore: registered new interface driver usb-storage
May 28 15:18:29 peter-OptiPlex-990 kernel: usbcore: registered new interface driver uas
May 28 15:18:29 peter-OptiPlex-990 upowerd[1639]: unhandled action 'bind' on /sys/devices/pci0000:00/0000:00:1d.0/usb2/2-1/2-1.8
May 28 15:18:29 peter-OptiPlex-990 upowerd[1639]: unhandled action 'bind' on /sys/devices/pci0000:00/0000:00:1d.0/usb2/2-1/2-1.8/2-1.8:1.0


```
which, I am afraid is complete greek to me.

---

### Post by pjstock on 2020-06-01
and now a 2nd USB external drive also does not Mount.

it too worked fine on another system. I suspected USB somthing? but other USB devices (like a scanner) work fine.0

strange that 2 USB HDDs would not be Mountable.

---

### Post by kneutron on 2020-06-05
> [COLOR=#000000][FONT=&amp][14980.311562] ready[/FONT][/COLOR][14980.312795] sd 6:0:0:0: [sdb] 488378645 4096-byte logical blocks: (2.00 TB/1.82 TiB)
[14980.312796] sd 6:0:0:0: [sdb] 16384-byte physical blocks
[14980.317044] sd 6:0:0:0: [sdb] Write Protect is off
[14980.317046] sd 6:0:0:0: [sdb] Mode Sense: 4f 00 00 00
[14980.317543] sd 6:0:0:0: [sdb] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[14980.317918] sd 6:0:0:0: [sdb] Optimal transfer size 268431360 bytes not a multiple of physical block size (16384 bytes)
[14980.340500]  sdb: sdb1
[14980.343294] sd 6:0:0:0: [sdb] Attached SCSI disk

--This means the kernel sees the disk and spun it up.  When you're having trouble mounting a disk, DO NOT RELY ON THE GUI.

As root:

' mkdir /mnt/tmp '
' mount /dev/sdb1 /mnt/tmp '

--At this point you should be able to access everything on the disk (AS ROOT) at /mnt/tmp.  If you need to, create a proper /etc/fstab entry for it instead of relying on automount or "Volume Management" in pcmanfm.

--If you can't access it properly, it may be a bad USB port on this particular PC. Try another one.

---

### Post by pjstock on 2020-06-11
though actually, and strangely, this 2nd HDD came back to life after a few days.
I don't know why that would happen but it was later recognized, mounted and accessible.

but #1 HDD still doesn't work. Actually another USB external drive also doesn't work on the problematic desktop.

---

### Post by pjstock on 2020-06-11
thanks for the tip to these Terminal commands.

mkdir /mnt/tmp
mount /dev/sdb1 /mnt/tmp

that's very clever. they does seem to allow me to these various external USB HDDs. at least temporarily. But only through Nautilius it seems.
I cannot access files on these HDDs to attach to an email for intance. 

I still like (need!) to work in the GUI world and i would like these HDDs to mount themselves automatically and be GUI-accessible.

so is this a work around or the best long term solution I can expect?
it seems a bit clumsy for the long term.

---

### Post by pjstock on 2020-06-11
I think my best plan of action now is just to backup and reinstall.

---

### Post by ActionParsnip on 2020-06-12
mount them to /media/tmp (make the folder first obviously)
Nautilus uses the /media folder to "see" external storage

---

### Post by pjstock on 2020-06-12
so, once I've manually mounted a drive in a folder under /media I guess it stays mounted. Until I have to reboot for some reason. at which time I just redo the Mkdir and Mount commands...?
a little bit clumsy but I guess I am not rebooting that often anyway.

and I see that with an external USB drive mounted under /media, Nautilius does see it and allow me to access it.

but I still cannot access it from my Thunderbird email service. I cannot reach into this location and Attach a file to an email for instance.
is there are way to work around That?

Peter

---

### Post by kneutron on 2020-06-13
> [COLOR=#000000]but I still cannot access it from my Thunderbird email service. I cannot reach into this location and Attach a file to an email for instance. [/COLOR][COLOR=#000000]is there are way to work around That?

--It depends on what filesystem you're using on the usb drives. If it's Linux-native like ext4, check your chown / chmod file permissions on those drives, they need to match the user you're logged in with - although root can access pretty much anything.[/COLOR]

---

### Post by rbmorse on 2020-06-13
Longshot:  unmount/eject and disconnect all external drives/storage devices.  In Nautilus, navigate to /media/*yourusername *and double click to open it.  There should be nothing there, but sometimes when a device is disconnected improperly or the system crashes a zombie mount point gets left behind.  That causes problems for the automounter. 

If you find files or folders in /media/*yourusername * make  sure once again that no external storage devices are connected then delete any and all files and folders inside /media/*yourusername.   *&#8203;Reboot.

---

