---
title: "Problems with Memory Stick"
date: 2005-09-06
forum: General Help
---

### Post by mtron on 2005-09-06
Hi! I have a problem with a quite new memory stick from Sony. It is a 128MB model what i use for my digital camera. The camera tells me that the device is "corrupt" what's strange cause yesterday i took some pictures, and everything worked fine.

Anyway i refused to believe it and plugged the card to a card reader. dmesg generates the following output:

usb 4-2: new high speed USB device using ehci_hcd and address 4
scsi2 : SCSI emulation for USB Mass Storage devices
usb-storage: device found at 4
usb-storage: waiting for device to settle before scanning
  Vendor: Generic   Model: STORAGE DEVICE    Rev: 9144
  Type:   Direct-Access                      ANSI SCSI revision: 00
usb 4-2: reset high speed USB device using ehci_hcd and address 4
scsi: Device offlined - not ready after error recovery: host 2 channel 0 id 0 lun 0
scsi2 (0:0): rejecting I/O to offline device
scsi2 (0:0): rejecting I/O to offline device
scsi2 (0:0): rejecting I/O to offline device
sda : READ CAPACITY failed.
sda : status=0, message=00, host=5, driver=04
sda : sense not available.
scsi2 (0:0): rejecting I/O to offline device
sda: Write Protect is off
sda: Mode Sense: 00 00 00 00
sda: assuming drive cache: write through
Attached scsi removable disk sda at scsi2, channel 0, id 0, lun 0
usb 4-2: reset high speed USB device using ehci_hcd and address 4
scsi: Device offlined - not ready after error recovery: host 2 channel 0 id 0 lun 1
usb-storage: device scan complete

When i try to mount it manually i get :
mount: /dev/sda is not a valid block device

can someone tell me a testing program that might show me some further information, or is the card, and all data on it really lost?

Cheers mtron.

---

