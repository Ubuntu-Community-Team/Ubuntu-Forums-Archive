---
title: "USB won't mount -- a common problem, it seems!"
date: 2007-10-23
forum: General Help
---

### Post by jmirick on 2007-10-23
Running 7.10 on a Dell Dimension 4600, I put in a USB stick and -- nothing.  Light goes on on the stick, it even flashes for a few moments, but no way can I see anything.  The drive mounts OK on a win machine.  Dmesg shows:

[INDENT][ 3870.619920] usb 5-8: new high speed USB device using ehci_hcd and address 3
[ 3870.768395] usb 5-8: configuration #1 chosen from 1 choice
[ 3870.769163] scsi5 : SCSI emulation for USB Mass Storage devices
[ 3870.769223] usb-storage: device found at 3
[ 3870.769225] usb-storage: waiting for device to settle before scanning
[ 3875.755363] usb-storage: device scan complete
[ 3875.756360] scsi 5:0:0:0: Direct-Access     Generic  STORAGE DEVICE   1.02 PQ: 0 ANSI: 0
[ 3876.012525] sd 5:0:0:0: [sdb] 256000 512-byte hardware sectors (131 MB)
[ 3876.129906] usb 5-8: reset high speed USB device using ehci_hcd and address 3
[ 3876.640601] usb 5-8: reset high speed USB device using ehci_hcd and address 3
[ 3877.147317] usb 5-8: reset high speed USB device using ehci_hcd and address 3
[ 3877.654023] usb 5-8: reset high speed USB device using ehci_hcd and address 3
[ 3878.160737] usb 5-8: reset high speed USB device using ehci_hcd and address 3
[ 3878.667458] usb 5-8: reset high speed USB device using ehci_hcd and address 3
[ 3878.807111] sd 5:0:0:0: [sdb] Write Protect is off
[ 3878.807116] sd 5:0:0:0: [sdb] Mode Sense: 02 00 00 00
[ 3878.807119] sd 5:0:0:0: [sdb] Assuming drive cache: write through
[ 3879.064740] sd 5:0:0:0: [sdb] 256000 512-byte hardware sectors (131 MB)
[ 3879.182133] usb 5-8: reset high speed USB device using ehci_hcd and address 3
[ 3879.692846] usb 5-8: reset high speed USB device using ehci_hcd and address 3
[ 3880.203535] usb 5-8: reset high speed USB device using ehci_hcd and address 3
[ 3880.714237] usb 5-8: reset high speed USB device using ehci_hcd and address 3
[ 3881.224937] usb 5-8: reset high speed USB device using ehci_hcd and address 3
[ 3881.735639] usb 5-8: reset high speed USB device using ehci_hcd and address 3
[ 3881.875323] sd 5:0:0:0: [sdb] Write Protect is off
[ 3881.875330] sd 5:0:0:0: [sdb] Mode Sense: 02 00 00 00
[ 3881.875333] sd 5:0:0:0: [sdb] Assuming drive cache: write through
[ 3881.875345]  sdb: sdb1
[ 3882.131161] sd 5:0:0:0: [sdb] Attached SCSI removable disk
[ 3882.131211] sd 5:0:0:0: Attached scsi generic sg2 type 0
[/INDENT]
dbus, hal, and Gnome-volume-manager are all installed.

Thoughts?

---

### Post by #Reistlehr- on 2007-10-23
try mounting it manually?

```

sudo mkdir /media/USB
sudo mount -t auto /dev/sdb /media/USB
sudo ln -s /media/USB /home/$USER/Desktop/USB

```

Just an idea of what to try..

---

### Post by maiden30403 on 2007-10-23
I have the same problem. Manual mount works fine but really I shouldn't have to resort to that IMO. I'll probably have to switch back to 6.06 again as the same bug was in 7.04 for me!

If anybody can offer me a solution it would be great though.

---

### Post by jmirick on 2007-10-23
Seemed to work, at least once; the link didn't work, though, but when I looked at nautilus, there it was, and it could read it.  Oh, and I had to make the second command say "sdb1" per what the dmsg said.  However, wouldn't dismount it, and then when I just removed it, then plugged it in again, it says it's there in nautilus but it can't access it.

When I redo your commands, the mkdir it rejects because the directory is still there.  That's correct, it is there.

then for      sudo mount -t auto /dev/sdb1 /media/USB   
it says:       mount: special device /dev/sdb1 does not exist

and the same thing if I use just /dev/sdb instead.

so, sort of getting there!

---

### Post by jmirick on 2007-10-23
Still no luck.  USB device icon is on screen but nothing behind it when you click, ditto when attempting to open in Nautilus, it says, "empty."

If I say,  mount usbdevfs
it says:
mount: can't find usbdevfs in /etc/fstab or /etc/mtab

USBView application sees nothing and can open nothing -- looking for the file /proc/bus/usb/devices
which isn't there.  Attempts to configure that to point to whatever is in /media/USB or in  
/dev/sdb or /dev/sdb1 don't work.

Removable Drives and Media application is set to "open everything when loaded" etc. but still nothing.

And, if I just pull the device out of the port, dmesg says:   [16248.567489] usb 5-8: USB disconnect, address 7
So it knows it's there, I just can't see it!

So, flummoxed.  I love Ubuntu and Linux in general but why should something this simple be so hard?

---

### Post by rykel on 2007-11-08
My USB mount used to work fine for a long time, until I deactivated dbus and/or hal a few days ago... now, even though I have reactivated/reconfigured hal, dbus, gnome-session, gnome-volume-manager etc. my USB drives just do not turn up on the desktop anymore...

Neither do I have the Hibernate and Suspend buttons in my logout dialog anymore.

Anyone can help? Thanks!!

---

