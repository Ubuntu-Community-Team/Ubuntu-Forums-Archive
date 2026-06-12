---
title: "Why won't my K750i automount any more?"
date: 2007-03-10
forum: General Help
---

### Post by gilgongo on 2007-03-10
I'm running Edgy and recently got a SonyEricsson K750i. At first, I was able to plug in the supplied USB cable, and got a nice little iPod icon on the desktop with which I could access the memorystick on the phone.

Now, for some reason, I can't any more. The only think that's changed is that I updated the firmware on the phone to the latest version using the Sony software updater under Windows, although since Sony's software is so awful, I don't know if it actually did anything or not. But since then, Ubuntu won't mount it.

This is what I get in /varl/log/messages when I plug it in:

Mar 10 18:41:25 monoplane kernel: [17179927.068000] usb 4-2: new full speed USB device using uhci_hcd and address 2
Mar 10 18:41:25 monoplane kernel: [17179927.332000] usb 4-2: configuration #1 chosen from 1 choice
Mar 10 18:41:25 monoplane kernel: [17179927.704000] usbcore: registered new driver libusual
Mar 10 18:41:25 monoplane kernel: [17179927.720000] Initializing USB Mass Storage driver...
Mar 10 18:41:25 monoplane kernel: [17179927.720000] scsi2 : SCSI emulation for USB Mass Storage devices
Mar 10 18:41:25 monoplane kernel: [17179927.720000] usbcore: registered new driver usb-storage
Mar 10 18:41:25 monoplane kernel: [17179927.720000] USB Mass Storage support registered.
Mar 10 18:41:25 monoplane kernel: [17179927.804000] cdc_acm 4-2:1.1: ttyACM0: USB ACM device
Mar 10 18:41:25 monoplane kernel: [17179927.808000] cdc_acm 4-2:1.3: ttyACM1: USB ACM device
Mar 10 18:41:25 monoplane kernel: [17179927.808000] usbcore: registered new driver cdc_acm
Mar 10 18:41:25 monoplane kernel: [17179927.808000] drivers/usb/class/cdc-acm.c: v0.25:USB Abstract Control Model driver for USB modems and ISDN adapters
Mar 10 18:41:30 monoplane kernel: [17179932.724000]   Vendor: Sony Eri  Model: Memory Stick      Rev: 0000
Mar 10 18:41:30 monoplane kernel: [17179932.724000]   Type:   Direct-Access                      ANSI SCSI revision: 00
Mar 10 18:41:30 monoplane kernel: [17179932.736000] SCSI device sdb: 126912 512-byte hdwr sectors (65 MB)
Mar 10 18:41:30 monoplane kernel: [17179932.740000] sdb: Write Protect is off
Mar 10 18:41:30 monoplane kernel: [17179932.748000] SCSI device sdb: 126912 512-byte hdwr sectors (65 MB)
Mar 10 18:41:30 monoplane kernel: [17179932.752000] sdb: Write Protect is off
Mar 10 18:41:30 monoplane kernel: [17179932.752000]  sdb: sdb1
Mar 10 18:41:30 monoplane kernel: [17179932.780000] sd 2:0:0:0: Attached scsi removable disk sdb
Mar 10 18:41:30 monoplane kernel: [17179932.780000] sd 2:0:0:0: Attached scsi generic sg1 type 0


Any ideas how I can get Ubuntu to recognise and mount it again like it used to a couple of days ago? I've tried powering everything down, switching USB ports, etc. but no joy.

---

### Post by Zkupa on 2007-05-03
Got nearly the same problem.
I havent updated the firmware, but i have upgraded to feisty since the last time i had the phone mounted (have been broken for some time)
Now it doesnt automount, and i have no idea how to mount it manually.

---

### Post by gh0st on 2007-05-03
I have a W810i and it seems to mount fine for me under Feisty. It might be worth check your settings in System / Preferences / Removable Drives & Media Preferences

Make sure the first 3 checkboxes are ticked. It's probably not that but I just thought I'd suggest it. You should also make sure you have the latest version of pmount installed, there was an update to fix a bug recently. When I moved to Feisty I couldn't Eject my USB hard disk at first, it seems they've patched this now, maybe they patched some other stuff too.

I know this is probably obvious but as a workaround you could always put the card from the phone in a card reader if you have one and see if it works. My printer has one on the front and I can transfer stuff to the memory card with that.

I dunno it that will help you much but you never know, good luck anyway hope you get it sorted soon :D

---

