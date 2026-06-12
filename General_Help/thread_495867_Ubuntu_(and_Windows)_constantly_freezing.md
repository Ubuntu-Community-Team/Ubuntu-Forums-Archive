---
title: "Ubuntu (and Windows) constantly freezing"
date: 2007-07-08
forum: General Help
---

### Post by Dimitrianos on 2007-07-08
I installed Ubuntu from the desktop CD with no problems.

Since Ubuntu has been installed both Ubuntu and Windows have been freezing.
All the colours become bluish and there are flickery lines on the screen.
This often happens on boot too.

I have taken some of the messages before it freezes:

(Freezing on boot)
```
Jul  8 18:41:24 hamish-desktop kernel: [   47.271173] pcc_acpi: loading...
Jul  8 18:41:27 hamish-desktop dhcdbd: Started up.
Jul  8 18:41:28 hamish-desktop dhcdbd: message_handler: message handler not found under /com/redhat/dhcp/eth0 for sub-path eth0.dbus.get.reason
Jul  8 18:41:28 hamish-desktop dhcdbd: message_handler: message handler not found under /com/redhat/dhcp/eth0 for sub-path eth0.dbus.get.reason
Jul  8 18:41:29 hamish-desktop kernel: [   53.232137] [drm] Initialized drm 1.1.0 20060810
Jul  8 18:41:29 hamish-desktop kernel: [   53.250468] ACPI: PCI Interrupt 0000:00:02.0[A] -> GSI 16 (level, low) -> IRQ 16
Jul  8 18:41:29 hamish-desktop kernel: [   53.254155] [drm] Initialized i915 1.6.0 20060119 on minor 0
Jul  8 18:41:30 hamish-desktop kernel: [   53.388540] ppdev: user-space parallel port driver
Jul  8 18:41:30 hamish-desktop hpiod: 1.7.3 accepting connections at 2208... 
Jul  8 18:41:31 hamish-desktop dhcdbd: message_handler: message handler not found under /com/redhat/dhcp/eth0 for sub-path eth0.dbus.get.host_name
Jul  8 18:41:31 hamish-desktop dhcdbd: message_handler: message handler not found under /com/redhat/dhcp/eth0 for sub-path eth0.dbus.get.domain_name
Jul  8 18:41:31 hamish-desktop dhcdbd: message_handler: message handler not found under /com/redhat/dhcp/eth0 for sub-path eth0.dbus.get.nis_domain
Jul  8 18:41:31 hamish-desktop dhcdbd: message_handler: message handler not found under /com/redhat/dhcp/eth0 for sub-path eth0.dbus.get.nis_servers
Jul  8 18:41:31 hamish-desktop kernel: [   54.632891] apm: BIOS version 1.2 Flags 0x07 (Driver version 1.16ac)
Jul  8 18:41:31 hamish-desktop kernel: [   54.632900] apm: overridden by ACPI.
Jul  8 18:41:31 hamish-desktop kernel: [   54.816609] Bluetooth: Core ver 2.11
Jul  8 18:41:31 hamish-desktop kernel: [   54.816709] NET: Registered protocol family 31
Jul  8 18:41:31 hamish-desktop kernel: [   54.816711] Bluetooth: HCI device and connection manager initialized
Jul  8 18:41:31 hamish-desktop kernel: [   54.816715] Bluetooth: HCI socket layer initialized
Jul  8 18:41:31 hamish-desktop kernel: [   54.870340] Bluetooth: L2CAP ver 2.8
Jul  8 18:41:31 hamish-desktop kernel: [   54.870347] Bluetooth: L2CAP socket layer initialized
Jul  8 18:41:31 hamish-desktop kernel: [   54.963938] Bluetooth: RFCOMM socket layer initialized
Jul  8 18:41:31 hamish-desktop kernel: [   54.963961] Bluetooth: RFCOMM TTY layer initialized
Jul  8 18:41:31 hamish-desktop kernel: [   54.963963] Bluetooth: RFCOMM ver 1.8
Jul  8 18:42:41 hamish-desktop syslogd 1.4.1#20ubuntu4: restart.
```

(Freezing on boot again, a few minutes afterwards)
```
Jul  8 18:44:07 hamish-desktop kernel: [   46.718592] pcc_acpi: loading...
Jul  8 18:44:10 hamish-desktop dhcdbd: Started up.
Jul  8 18:44:10 hamish-desktop dhcdbd: message_handler: message handler not found under /com/redhat/dhcp/eth0 for sub-path eth0.dbus.get.reason
Jul  8 18:44:10 hamish-desktop dhcdbd: message_handler: message handler not found under /com/redhat/dhcp/eth0 for sub-path eth0.dbus.get.reason
Jul  8 18:44:12 hamish-desktop kernel: [   52.346237] [drm] Initialized drm 1.1.0 20060810
Jul  8 18:44:12 hamish-desktop kernel: [   52.365472] ACPI: PCI Interrupt 0000:00:02.0[A] -> GSI 16 (level, low) -> IRQ 16
Jul  8 18:44:12 hamish-desktop kernel: [   52.369036] [drm] Initialized i915 1.6.0 20060119 on minor 0
Jul  8 18:44:12 hamish-desktop kernel: [   52.461888] ppdev: user-space parallel port driver
Jul  8 18:44:13 hamish-desktop hpiod: 1.7.3 accepting connections at 2208... 
Jul  8 18:44:13 hamish-desktop dhcdbd: message_handler: message handler not found under /com/redhat/dhcp/eth0 for sub-path eth0.dbus.get.host_name
Jul  8 18:44:13 hamish-desktop dhcdbd: message_handler: message handler not found under /com/redhat/dhcp/eth0 for sub-path eth0.dbus.get.domain_name
Jul  8 18:44:13 hamish-desktop dhcdbd: message_handler: message handler not found under /com/redhat/dhcp/eth0 for sub-path eth0.dbus.get.nis_domain
Jul  8 18:44:13 hamish-desktop dhcdbd: message_handler: message handler not found under /com/redhat/dhcp/eth0 for sub-path eth0.dbus.get.nis_servers
Jul  8 18:44:13 hamish-desktop kernel: [   53.747473] apm: BIOS version 1.2 Flags 0x07 (Driver version 1.16ac)
Jul  8 18:44:13 hamish-desktop kernel: [   53.747481] apm: overridden by ACPI.
Jul  8 18:44:13 hamish-desktop kernel: [   53.939278] Bluetooth: Core ver 2.11
Jul  8 18:44:13 hamish-desktop kernel: [   53.939386] NET: Registered protocol family 31
Jul  8 18:44:13 hamish-desktop kernel: [   53.939389] Bluetooth: HCI device and connection manager initialized
Jul  8 18:44:13 hamish-desktop kernel: [   53.939394] Bluetooth: HCI socket layer initialized
Jul  8 18:44:13 hamish-desktop kernel: [   53.991054] Bluetooth: L2CAP ver 2.8
Jul  8 18:44:13 hamish-desktop kernel: [   53.991062] Bluetooth: L2CAP socket layer initialized
Jul  8 18:44:13 hamish-desktop kernel: [   54.085385] Bluetooth: RFCOMM socket layer initialized
Jul  8 18:44:13 hamish-desktop kernel: [   54.085407] Bluetooth: RFCOMM TTY layer initialized
Jul  8 18:44:13 hamish-desktop kernel: [   54.085410] Bluetooth: RFCOMM ver 1.8
```

Since this freeze Ubuntu hasn't been able to start up without crashing and I am now using Windows, which also freezes.
I can't access the event viewer in Windows but I imagine it's freezing for the same reason as Ubuntu is.

I need to solve this problem soon, as my computer is crashing all the time it's very hard to use.
Any help would be much appreciated.

Dimitrianos.

EDIT: Forgot my system specs:

Pentium4 2.8Ghz
512MB RAM
Intel 456G Chipset
On-board Video card

---

### Post by Dimitrianos on 2007-07-08
I'm going to bump this thread, I hope it's not against the rules.

---

### Post by ahaslam on 2007-07-08
Does it always freeze at the same point?

---

### Post by Dimitrianos on 2007-07-08
If it freezes on boot it always freezes just after the loading screen, just when the pointer shows it freezes.
If it survives boot then it can freeze at any time.

---

### Post by Mr. C. on 2007-07-08
Sounds like a hardware problem.

Have you run diagnostics on your RAM, motherboard, etc. ?

MrC

---

### Post by Absorbed on 2007-07-08
I had a similar problem on two occasions, where my computer would never boot properly. It would always freeze before I got to the desktop, and even if I did get to the desktop it would freeze before long. Replacing my PSU fixed it both times. If that is similar to your situations, as you seemed to suggest it freezed on linux and windows, then this is a possible cause.

---

### Post by Loffe_ on 2007-07-08
I had similar random freezes some time ago. My problem was a wasted RAM module.

When grub shows up choose Memtest in the list. It will test your RAM and tell you if your memory is defective.

- Loffe

---

### Post by Dimitrianos on 2007-07-09
Memtest crashed when it was at 55%, no errors.
Computer just switched off.

---

### Post by Loffe_ on 2007-07-09
> **Dimitrianos said:**
> Memtest crashed when it was at 55%, no errors.
Computer just switched off.

Do you have multiple memory modules? If so remove one of them and run memtest again.

Try memtest with one memory module at a time...

It's definitely a hardware problem.

- Loffe

---

### Post by Dimitrianos on 2007-07-09
Okay, I'll get back to you once I've finished.

---

### Post by Swankyman on 2007-07-09
Also make sure you cpus fan is working and kicking out hot air. Otherwise over temp protection might be kicking in and turning everything off

:confused:

rich

---

### Post by Dimitrianos on 2007-07-10
Okay, I tested each memory one by one and found the faulty one.
I've removed it now and it's working fine.

---

### Post by Loffe_ on 2007-07-15
Good to hear you found the problem.

There is a good chance you can get a new module on the warranty. 

- Loffe

---

