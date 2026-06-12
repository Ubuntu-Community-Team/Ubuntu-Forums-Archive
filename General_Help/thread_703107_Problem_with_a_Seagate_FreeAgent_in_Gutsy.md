---
title: "Problem with a Seagate FreeAgent in Gutsy"
date: 2008-02-21
forum: General Help
---

### Post by soapman on 2008-02-21
Up until yesterday, my FreeAgent 320GB drive was working fine - still with its original NTFS partition and I hadn't yet bothered to search for a solution to the spindown/random unmounting problem that seems common with these drives.

Today when I tried to access the drive (which had been unplugged overnight), it didn't try to automount and it didn't appear in kde's "media" window (or get given a device). So I did a dmesg to see what (if anything) was happening. When I plug the drive in, this message appears in dmesg:

<deleted - see below>

The 'address' changes depending on which USB port I plug in to. 

I plugged it in to the laptop (running windows vista) to see if it was a fault with the FreeAgent, but windows detected,mounted,accessed the drive perfectly. I ran checkdisk while it was plugged in to the laptop to make sure there were no filesystem errors preventing linux from mounting the drive, and it fixed a couple of minor errors. Plugged it back in to the linux box to see if anything had changed, but still the same error.

please help - I tried googling the error but either I'm googling the wrong thing or I have a unique problem.

Thanks in advance :)


Some extra info on what I've looked in to. I've seen similar errors reported in relation to the ehci_hcd module and I have tried having the ohci_hcd module mount it by unloading ehci_hcd, but all that changes is the error message slightly. It seems I also missed part of the error message in my original post. Here is the full message:
[ 6855.854779] usb 1-5: new high speed USB device using ehci_hcd and address 12
[ 6856.262641] usb 1-5: device not accepting address 12, error -32
[ 6856.374636] usb 1-5: new high speed USB device using ehci_hcd and address 13
[ 6856.782496] usb 1-5: device not accepting address 13, error -32
[ 6856.894481] usb 1-5: new high speed USB device using ehci_hcd and address 14
[ 6857.006455] usb 1-5: device descriptor read/64, error -32
[ 6857.222441] usb 1-5: device descriptor read/64, error -32
[ 6857.438325] usb 1-5: new high speed USB device using ehci_hcd and address 15
[ 6857.550295] usb 1-5: device descriptor read/64, error -32
[ 6857.766236] usb 1-5: device descriptor read/64, error -32

I've googled 'descriptor read/64' which led me to the whole ehci_hcd thing, but that hasn't helped me at all.. I'm really stumped now. Going to try re-installing udev to see if that helps... don't see how it will though!

---

