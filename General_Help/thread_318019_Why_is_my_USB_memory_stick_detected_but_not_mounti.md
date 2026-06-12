---
title: "Why is my USB memory stick detected but not mounting?"
date: 2006-12-13
forum: General Help
---

### Post by tmastran on 2006-12-13
Why is my USB memory stick detected but not mounting?

This is on dapper.
If I plug in the memory stick and then remove it I get these message in /var/log/messages:

$ tail /var/log/messages
Dec 13 10:30:53 localhost kernel: [17180335.920000] usb 1-9: new high speed USB device using ehci_hcd and address 5
Dec 13 10:31:12 localhost kernel: [17180354.328000] usb 1-9: USB disconnect, address 5

So the device is being detected?

df -h before and after is the same:
$ df -h
Filesystem Type    Size Used Avail Use% Mounted on
/dev/sdb5     ext3     12G  5.1G  6.0G  46% /
varrun       tmpfs   1013M  184K 1013M   1% /var/run
varlock      tmpfs   1013M  4.0K 1013M   1% /var/lock
udev         tmpfs   1013M  136K 1013M   1% /dev
devshm       tmpfs   1013M     0 1013M   0% /dev/shm
/dev/sdb7     ext3     25G  9.6G   14G  42% /home
/dev/sda1     ntfs    233G   38G  196G  16% /media/sda1
/dev/sdb1     ntfs     49G   20G   29G  41% /media/sdb1
/dev/sdb3     vfat     20G   32K   20G   1% /media/fat32
/dev/sdb4     ext3    124G   85G   32G  73% /media/data

lsusb before and after is:
$ lsusb
Bus 002 Device 003: ID 046d:c50d Logitech, Inc.
Bus 002 Device 002: ID 046d:c30a Logitech, Inc.
Bus 002 Device 001: ID 0000:0000
Bus 001 Device 001: ID 0000:0000

lspci shows:
$ lspci -v | grep USB
0000:00:02.0 USB Controller: nVidia Corporation CK804 USB Controller (rev a2) (prog-if 10 [OHCI])
0000:00:02.1 USB Controller: nVidia Corporation CK804 USB Controller (rev a3) (prog-if 20 [EHCI])

Any ideas? The device works on the same hardware booted into another OS.
Thanks

---

### Post by taurus on 2006-12-13
Maybe you just have to mount it by hand.  Plug it in and paste this message from a terminal here!

```
dmesg | tail
```

---

### Post by tmastran on 2006-12-13
I get the same thing I got from /var/log/messages:

[17181415.532000] usb 1-9: new high speed USB device using ehci_hcd and address 8

I'm not sure what to mount by hand? There is no device assignment?

---

### Post by duva on 2006-12-13
Has anyone gotten further than this point? I seem to have the same problem.  How to know which device to mount?

---

### Post by tmastran on 2006-12-14
> **duva said:**
> Has anyone gotten further than this point? I seem to have the same problem.  How to know which device to mount?

No. I'm still stuck. I love Ubuntu a lot, but have never had much luck with USB devices on Linux. I have cameras and palm pilots that don't work quite right either.

All I need is a good nudge in the right direction...

---

### Post by dcstar on 2006-12-14
> **tmastran said:**
> No. I'm still stuck. I love Ubuntu a lot, but have never had much luck with USB devices on Linux. I have cameras and palm pilots that don't work quite right either.

All I need is a good nudge in the right direction...

The same thing happened to my 6.06 install after the updates the other day, but now it is back working ok again! (I guess another update to the update must have been sent out).

Is yours still broken?

---

### Post by tmastran on 2006-12-14
> **dcstar said:**
> The same thing happened to my 6.06 install after the updates the other day, but now it is back working ok again! (I guess another update to the update must have been sent out).

Is yours still broken?

Yes, but I haven't applied the 2006-12-14 updates yet. Waiting for the dust to settle. From my earlier posts you can see that the system detects the memory stick being inserted, but does not assign (or create?) a device for it. I don't know enough about this part of Linux to know if this is something with "udev" or "hotplug". Like I said earlier a nudge in the right direction would help. I've read somewhere else that it might be IRQ's, but don't know what to do next?

---

### Post by dcstar on 2006-12-15
> **tmastran said:**
> Yes, but I haven't applied the 2006-12-14 updates yet. Waiting for the dust to settle. From my earlier posts you can see that the system detects the memory stick being inserted, but does not assign (or create?) a device for it. I don't know enough about this part of Linux to know if this is something with "udev" or "hotplug". Like I said earlier a nudge in the right direction would help. I've read somewhere else that it might be IRQ's, but don't know what to do next?

I would recommend putting them all on, apparently an update to the HAL sub-system fixes these things.

As far as finding out what causes it (in log files etc.), good luck (I have given up!)

---

### Post by tmastran on 2006-12-15
> **dcstar said:**
> I would recommend putting them all on, apparently an update to the HAL sub-system fixes these things.

As far as finding out what causes it (in log files etc.), good luck (I have given up!)

I applied all the updates and rebooted and now the memory stick is detected and mounted. dmesg shows this difference now:

Dec 15 17:39:08 delphi kernel: [17179768.924000] usb 5-8: new high speed USB device using ehci_hcd and address 2
Dec 15 17:39:08 delphi kernel: [17179769.060000] usb 5-8: configuration #1 chosen from 1 choice
Dec 15 17:39:08 delphi kernel: [17179769.144000] usbcore: registered new driver libusual
Dec 15 17:39:09 delphi kernel: [17179769.168000] Initializing USB Mass Storage driver...
Dec 15 17:39:09 delphi kernel: [17179769.168000] scsi2 : SCSI emulation for USB Mass Storage devices
Dec 15 17:39:09 delphi kernel: [17179769.168000] usbcore: registered new driver usb-storage
Dec 15 17:39:09 delphi kernel: [17179769.168000] USB Mass Storage support registered.
Dec 15 17:39:14 delphi kernel: [17179774.196000]   Vendor: SanDisk   Model: Cruzer Mini       Rev: 0.2
Dec 15 17:39:14 delphi kernel: [17179774.196000]   Type:   Direct-Access                      ANSI SCSI revision: 02
Dec 15 17:39:14 delphi kernel: [17179774.196000] SCSI device sdc: 2001888 512-byte hdwr sectors (1025 MB)
Dec 15 17:39:14 delphi kernel: [17179774.200000] sdc: Write Protect is off
Dec 15 17:39:14 delphi kernel: [17179774.200000] SCSI device sdc: 2001888 512-byte hdwr sectors (1025 MB)
Dec 15 17:39:14 delphi kernel: [17179774.204000] sdc: Write Protect is off
Dec 15 17:39:14 delphi kernel: [17179774.204000]  sdc: sdc1
Dec 15 17:39:14 delphi kernel: [17179774.204000] sd 2:0:0:0: Attached scsi removable disk sdc
Dec 15 17:39:14 delphi kernel: [17179774.204000] sd 2:0:0:0: Attached scsi generic sg2 type 0

Which looks good! And device sdc1 is auto-mounted to /media/usbstick.

Thanks for your help.
Ted

---

### Post by tmastran on 2006-12-30
> **tmastran said:**
> I applied all the updates and rebooted and now the memory stick is detected and mounted. dmesg shows this difference now:

Dec 15 17:39:08 delphi kernel: [17179768.924000] usb 5-8: new high speed USB device using ehci_hcd and address 2
Dec 15 17:39:08 delphi kernel: [17179769.060000] usb 5-8: configuration #1 chosen from 1 choice
Dec 15 17:39:08 delphi kernel: [17179769.144000] usbcore: registered new driver libusual
Dec 15 17:39:09 delphi kernel: [17179769.168000] Initializing USB Mass Storage driver...
Dec 15 17:39:09 delphi kernel: [17179769.168000] scsi2 : SCSI emulation for USB Mass Storage devices
Dec 15 17:39:09 delphi kernel: [17179769.168000] usbcore: registered new driver usb-storage
Dec 15 17:39:09 delphi kernel: [17179769.168000] USB Mass Storage support registered.
Dec 15 17:39:14 delphi kernel: [17179774.196000]   Vendor: SanDisk   Model: Cruzer Mini       Rev: 0.2
Dec 15 17:39:14 delphi kernel: [17179774.196000]   Type:   Direct-Access                      ANSI SCSI revision: 02
Dec 15 17:39:14 delphi kernel: [17179774.196000] SCSI device sdc: 2001888 512-byte hdwr sectors (1025 MB)
Dec 15 17:39:14 delphi kernel: [17179774.200000] sdc: Write Protect is off
Dec 15 17:39:14 delphi kernel: [17179774.200000] SCSI device sdc: 2001888 512-byte hdwr sectors (1025 MB)
Dec 15 17:39:14 delphi kernel: [17179774.204000] sdc: Write Protect is off
Dec 15 17:39:14 delphi kernel: [17179774.204000]  sdc: sdc1
Dec 15 17:39:14 delphi kernel: [17179774.204000] sd 2:0:0:0: Attached scsi removable disk sdc
Dec 15 17:39:14 delphi kernel: [17179774.204000] sd 2:0:0:0: Attached scsi generic sg2 type 0

Which looks good! And device sdc1 is auto-mounted to /media/usbstick.

Thanks for your help.
Ted

UPDATE - This works for a while, but if I leave the machine up for a while, the device is no longer detected and I have to boot. It´s like some sub-system has stopped responding.

When I plug in a SanDisk mp3 player the display says USB Connected, so the device knows it plugged in but Ubuntu doesn´t.

It´s kind of a pain to have to reboot just to plug in a USB device. Any ideas what is wrong?  Is there some reset command I could try? Getting kind of frustrated since USB works correctly on the same box in windows xp.

---

### Post by ExemplarUbuntu on 2007-01-05
I think I have a similar problem to this.

I had a seriously problematic upgrade to Breezy and now USB sticks aren't mounted.

syslog says that the kernel is detecting the sda disk and that sd_mod is loaded successfully. However, the normal USB icon doesn't appear on the desktop.

I just did an update to make sure I had an up-to-date Breezy. It updated 54 modules, a few libs but mostly python. Didn't see HAL mentioned.

Edit: after that update it showed a problem with the dists list which I corrected and got about 160 more updates but still no change.
I did manage to mount it manually as root but then it is read only.

---

### Post by Wanderers on 2007-01-06
I am having the same problem. I recently updgraded from Breezy to Dapper and since then Ubuntu does not automount my USB memory stick anymore.  

lsusb shows the drive, but when I try to mount /dev/sda1, I get an errormessage that this is not a block device.  My system has all the latest upgrades installed.

Although I find my way around Linux, I am not a Linux specialist and I do not know how to progress this further, particularly not because a manual mount does not work.

Has anyone found a reliable solution for this problem? Would it help to upgrade to Edgy?

---

### Post by wanger123 on 2007-01-08
me too, me too!!!


[EDIT] I just fixed this.  I had to add the repository: deb [http://kubuntu.org/packages/kde-355](http://kubuntu.org/packages/kde-355) dapper main

from the kubuntu website ([http://kubuntu.org/announcements/kde-355.php](http://kubuntu.org/announcements/kde-355.php)) then update and upgrade and it replaced 3 ubuntu libhal and hal files with 3 kubuntu versions

cheers 


wanger

---

### Post by ExemplarUbuntu on 2007-01-08
I am not using kubuntu so is it ok to do this ?

---

### Post by wanger123 on 2007-01-08
I spoke too soon as usual. When I plug in my usb stick it is auto mounted (after about 20secs) but I can't unmount it in any way. If I copy something to it I have to wait like 15-20 secs before it does anything. This is absolute crap!!!!!!!!!


wanger123

---

### Post by ExemplarUbuntu on 2007-01-09
What I have discovered is that when a usb dongle is plugged in, inside System Monitor I can see the new Device. In fact they accumulate, I have plugged the same dongle 3 times and now I see three devices sda1, sdb1 and sdc1

I am able to manually mount the "disc" but can't write to it due to permissions. (unless I use sudo from the cli)

I had a look at Gnome Vol Manager in synaptic. It says it's not installed but it I couldn't install it due to HAL and that in turn wouldn't install due to dbus.

When I looked at dbus it wanted to remove Gnome, gtk and lots of other things and I am not doing that.

This is silly. Hotplugging worked in earlier versions, what went wrong.

---

### Post by dcstar on 2007-01-09
> **ExemplarUbuntu said:**
> ........
I had a look at Gnome Vol Manager in synaptic. It says it's not installed but it I couldn't install it due to HAL and that in turn wouldn't install due to dbus.
........

It seems that some of these issues are due to gnome-volume-manager not starting on boot-up.

I have found in my 6.10 system that turning off the Gnome Splash option stops this process (and at least one other) from starting automatically, so when I plug in my USB drive the SCSI sub-system detects it, but it is not auto-mounted.

When I turn the splash option back on (System-Preferences-Sessions), all things work as normal..........

---

### Post by ExemplarUbuntu on 2007-01-10
I have the splash screen switched on all ready.

How can I tell if gvm is running ? I can't see anything called gvm in System Monitor and ps -A doesn't show anything that looks like it.

---

### Post by dcstar on 2007-02-03
> **ExemplarUbuntu said:**
> I have the splash screen switched on all ready.

How can I tell if gvm is running ? I can't see anything called gvm in System Monitor and ps -A doesn't show anything that looks like it.

The problem seems to be caused by a timing issue where the desktop is loaded (by auto-login) before essential processes have fully loaded on boot, my solution is:

   1. Leave Auto-login enabled
   2. Edit /etc/default/rcS and set the relevant line to: "DELAYLOGIN=YES"

This delays certain login processes until previous ones are completed, and seems to ensure that (on my system, at least) that my USB stick drive is mounted and available on every boot-up.

---

### Post by ExemplarUbuntu on 2007-02-26
It didn't make any visible difference on my system. I can manually mount the USB stick
as root but that really limits what you can do.

---

