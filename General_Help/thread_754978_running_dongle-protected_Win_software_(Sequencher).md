---
title: "running dongle-protected Win software (Sequencher) using wine"
date: 2008-04-14
forum: General Help
---

### Post by Cynarina on 2008-04-14
I am trying to run a Windows software (Sequencher) that is protected with a Sentinel SuperPro USB dongle (if no dongle is inserted, the software will only run in demo mode, which means that you cannot save the result of your work).  I have installed the usbdaemon driver provided by the key manufacturer (SafeNet), the USB dongle is apparently detected by my computer (judging from the dmesg output:
[21831.828000] usb 2-2: new low speed USB device using uhci_hcd and address 2
[21832.000000] usb 2-2: configuration #1 chosen from 1 choice
after I insert the SuperPro key, and
[21921.808000] usb 2-2: USB disconnect, address 2
after I remove it); Sequencher is working beautifully under Wine or Crossover but, alas, in demo mode only as it does not detect the dongle!

I have contacted the software company (GeneCodes), but all they replied is that they were surprised to hear that their software would run under Linux in the first place...

---

### Post by Cynarina on 2008-04-22
Finally the only way I found to run the software in full mode was to install VMware server 2.0 beta2 and make a full Windows XP install within a virtual machine. Now the dongle is detected, but it is of course much slower and cumbersome than running the software directly using wine!

Let's hope there will be some work done on SuperPro support in wine in the future...

---

