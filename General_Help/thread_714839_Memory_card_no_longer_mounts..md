---
title: "Memory card no longer mounts."
date: 2008-03-04
forum: General Help
---

### Post by jsedwards on 2008-03-04
I have Compact Flash cards from my camera and up until now I have been able to plug them into the build in card reader in my Dell Inspiron 530 and Kubuntu 7.10 detected and mounted them just fine.  (It has probably been a month or so since I last did this).

Yesterday, I plugged the CompactFlash card into the built in reader and the light on the reader started flashing.  And it kept flashing for several minutes and nothing else happened.  After 4 or 5 minutes I took it out and plugged it into the external card reader (which I used before I bought the Dell Inspiron).  Nothing happened at all the light didn't even go on.

At this point I decided to look at the output of dmesg and see if there was any hints as to the problem there.  It was spewing messages about some usb stuff (I didn't write them down at the time so I can't say exactly what they said).  So I finally unplugged the external card reader altogether to see if the messages stopped and they didn't.  It was spewing the same messages to /var/log/messages.  A-ha, I'll bet the messages are still in the log...  yes these are the messages it was spewing yesterday:

[FONT="Courier New"]Mar  3 05:13:56 inspiron kernel: [84340.197625] usb 7-4: new high speed USB device using ehci_hcd and address 5
Mar  3 05:13:56 inspiron kernel: [84340.330931] usb 7-4: configuration #1 chosen from 1 choice
Mar  3 05:13:56 inspiron kernel: [84340.635460] /build/buildd/linux-source-2.6.22-2.6.22/drivers/usb/class/usblp.c: usblp0
: USB Bidirectional printer dev 5 if 1 alt 0 proto 2 vid 0x04B8 pid 0x0812
Mar  3 05:13:56 inspiron kernel: [84340.635482] usbcore: registered new interface driver usblp
Mar  3 05:13:56 inspiron kernel: [84340.635486] /build/buildd/linux-source-2.6.22-2.6.22/drivers/usb/class/usblp.c: v0.13:
 USB Printer Device Class driver
Mar  3 05:43:38 inspiron kernel: [86121.361965] usb 7-4: USB disconnect, address 5
Mar  3 05:43:38 inspiron kernel: [86121.362356] /build/buildd/linux-source-2.6.22-2.6.22/drivers/usb/class/usblp.c: usblp0
: removed
Mar  3 06:20:16 inspiron kernel: [88317.909668] usb 8-5: USB disconnect, address 2
Mar  3 06:20:17 inspiron kernel: [88318.529106] usb 8-5: new high speed USB device using ehci_hcd and address 5
Mar  3 06:20:17 inspiron kernel: [88319.016820] usb 8-5: new high speed USB device using ehci_hcd and address 7
Mar  3 06:20:18 inspiron kernel: [88319.504535] usb 8-5: new high speed USB device using ehci_hcd and address 9
Mar  3 06:20:18 inspiron kernel: [88320.368034] usb 8-5: new high speed USB device using ehci_hcd and address 13
Mar  3 06:20:19 inspiron kernel: [88320.855749] usb 8-5: new high speed USB device using ehci_hcd and address 15[/FONT]

Those last ones were repeated 6724 times (the address increased up to 127 and then started over) until I powered it off.

I then plugged the external reader with the Compact Flash card into my Wife's MacBook and it mounted the Memory Card just fine and everything looked normal.

Today, I booted my machine up and plugged the Compact Flash card into the built in reader.  Nothing happened, the light did not come on at all.

I checked dmesg and these messages happened when I plugged it in:

[FONT="Courier New"][  352.670536] usb 8-5: USB disconnect, address 2
[  353.218280] usb 6-1: new full speed USB device using uhci_hcd and address 2
[  353.338211] usb 6-1: device descriptor read/64, error -71
[  353.562072] usb 6-1: device descriptor read/64, error -71
[  353.777949] usb 6-1: new full speed USB device using uhci_hcd and address 3
[  353.897875] usb 6-1: device descriptor read/64, error -71
[  354.121743] usb 6-1: device descriptor read/64, error -71
[  354.337615] usb 6-1: new full speed USB device using uhci_hcd and address 4
[  354.745365] usb 6-1: device not accepting address 4, error -71
[  354.857304] usb 6-1: new full speed USB device using uhci_hcd and address 5
[  355.265054] usb 6-1: device not accepting address 5, error -71[/FONT]

I then removed the CF card from the built in reader and plugged it into the external card reader and nothing happened, not even any futher messages from dmesg.

Other than upgrades with Adept Manager I don't think I have made any changes to the machine since the last time reading the memory card worked.  I haven't changed the hardware at all.

Thanks for any suggestions.
  -Scott

---

### Post by mgranet on 2008-03-04
Were you unmounting the card before removing it? If not, you might have corrupted the card's filesystem

---

### Post by jsedwards on 2008-03-05
I am always very careful to unmount anything before removing it.  And as I said the memory card works fine in the camera and on my Wife's MacBook.  I just tried two other memory cards and it didn't recognize them either.  I'm fairly certain that the memory cars are okay.

My guess would be that if the memory card was corrupted it would still detect that I had inserted it and attempt to mount it?  It doesn't even seem to recognize that I have inserted anything.  I will try rebooting again later and see what it does after a reboot, but I have to get ready for work now.

---

### Post by damytzeus on 2008-03-22
Same thing happened to my Inspiron 530.  Within the last two weeks, it appears that the card reader no longer works.  It doesn't even light up.  It sounds like perhaps a software update could have broken it.

Any ideas??

---

### Post by jsedwards on 2008-04-05
I am so sorry, I intended to post a new message to this thread, saying that I powered my machine off for a while (and I may have updated the system again, now I can't remember).  When I turned it back on it worked just fine.  I haven't had any problem since, I just mounted a memory card a couple of days ago and it worked perfectly.

---

### Post by nikolajsheller on 2008-06-30
Hi

I'm seeing this on two different machines (64 bit) when attempting to mount my Garmin Nuvi 250 GPS. 

Jun 30 19:25:16 MiniMe kernel: [341334.770837] usb 1-1: new full speed USB device using uhci_hcd and address 37
Jun 30 19:25:17 MiniMe kernel: [341334.862879] usb 1-1: device descriptor read/64, error -71
Jun 30 19:25:17 MiniMe kernel: [341335.090846] usb 1-1: device descriptor read/64, error -71
Jun 30 19:25:17 MiniMe kernel: [341335.306805] usb 1-1: new full speed USB device using uhci_hcd and address 38
Jun 30 19:25:17 MiniMe kernel: [341335.426783] usb 1-1: device descriptor read/64, error -71
Jun 30 19:25:17 MiniMe kernel: [341335.654895] usb 1-1: device descriptor read/64, error -71
Jun 30 19:25:18 MiniMe kernel: [341335.870137] usb 1-1: new full speed USB device using uhci_hcd and address 39
Jun 30 19:25:18 MiniMe kernel: [341336.282636] usb 1-1: device not accepting address 39, error -71
Jun 30 19:25:18 MiniMe kernel: [341336.394617] usb 1-1: new full speed USB device using uhci_hcd and address 40
Jun 30 19:25:18 MiniMe kernel: [341336.810533] usb 1-1: device not accepting address 40, error -71

---

