---
title: "Feisty strange USB problems"
date: 2007-04-22
forum: General Help
---

### Post by mwaddoups on 2007-04-22
I recently installed Feisty, and I have been having some very strange problems with USB devices. I have a USB keyboard/mouse, as well as a USB flash disk. When I plugged in this flash disk when I first installed the system, it was detected and mounted fine. After a couple of reboots, whenever I plugged in this or any USB device, it caused my keyboard and mouse to stop working. I had a terminal open at the time, and the output read "Disabling IRQ #18...". The OS doesn't seem to have crashed, but simply something is disabling my USB.

A similar thing happens when I plug in my USB wireless adaptor - the entire system freezes up, and I get no output messages in the console. I have not been able to update the OS, as I have not been able to connect to the internet yet. I have tried two boot options that apparently fix this - "acpi=force irqpoll" which did nothing, and "noapic" which stops the system from booting with an error about IRQ handler #0 (yet fixes some earlier error messages about bugs). Any ideas on how I could fix this?

---

### Post by mwaddoups on 2007-04-22
An update:

I tried again with the "irqpoll" boot option, and it stopped the Disabling IRQ #18 error - I also noticed I was getting a Disabling IRQ #16 error on boot and that recommended irqpoll. However, whenever I plug ANY usb device in, the system slows down considerably so that it is not possible to use it, and the usb device is mounted as a cdrom, and a message box comes up saying "There are video and music files on this CD-ROM" - this is not just with my flash drive! I then get an error about "invalid mount operation" with my flash drive.

Thanks.

---

### Post by mwaddoups on 2007-04-22
Here is the output to "cat /proc/interrupts" after the USB flash drive has been plugged in (I used a USB to PS/2 converter for my mouse):
```
           
CPU0       
  0:      81626  local-APIC-edge-fasteio   timer
  1:          2   IO-APIC-edge      i8042
  6:          2   IO-APIC-edge      floppy
  8:          3   IO-APIC-edge      rtc
 12:      32344   IO-APIC-edge      i8042
 14:       9133   IO-APIC-edge      ide0
 16:          0   IO-APIC-fasteoi   libata, libata
 17:          0   IO-APIC-fasteoi   libata
 18:     200073   IO-APIC-fasteoi   ohci_hcd:usb1, ohci_hcd:usb2, ehci_hcd:usb3
 19:        858   IO-APIC-fasteoi   eth1, saa7146 (0), HDA Intel
 20:          2   IO-APIC-fasteoi   ohci1394
 21:          1   IO-APIC-fasteoi   acpi, eth0
 22:      30946   IO-APIC-fasteoi   radeon@pci:0000:01:00.0
NMI:          0 
LOC:      81518 
ERR:          0

MIS:          0

```

Also here is the output that appears in the system log when it is plugged in:

```
[  157.542622]  [__report_bad_irq+36/128] __report_bad_irq+0x24/0x80
[  157.542638]  [run_timer_softirq+55/416] run_timer_softirq+0x37/0x1a0
[  157.542645]  [note_interrupt+606/656] note_interrupt+0x25e/0x290
[  157.542671]  [<f885ef32>] usb_hcd_irq+0x22/0x60 [usbcore]
[  157.542695]  [handle_IRQ_event+48/96] handle_IRQ_event+0x30/0x60
[  157.542714]  [handle_fasteoi_irq+193/240] handle_fasteoi_irq+0xc1/0xf0
[  157.542732]  [do_IRQ+64/128] do_IRQ+0x40/0x80
[  157.542754]  [common_interrupt+35/48] common_interrupt+0x23/0x30
[  157.542760]  [default_idle+0/96] default_idle+0x0/0x60
[  157.542798]  [native_safe_halt+2/16] native_safe_halt+0x2/0x10
[  157.542809]  [default_idle+61/96] default_idle+0x3d/0x60
[  157.542811]  [cpu_idle+73/208] cpu_idle+0x49/0xd0
[  157.542825]  [start_kernel+869/1056] start_kernel+0x365/0x420
[  157.542833]  [unknown_bootoption+0/608] unknown_bootoption+0x0/0x260

```

Hope somebody has some idea about this! As you can see from the /proc/interrupts, all the usb devices are on IRQ #18 - is there a way to assign IRQ's in Ubuntu, so I could perhaps give them a different IRQ? I've been working on this all day:( .

EDIT: I disabled SATA completely in the bios due to the information from a different thread, and the disabling IRQ message changed from IRQ #18 to IRQ #16, as did all the usb devices according to /proc/interrupts. If I boot using the irqpoll option in this configuration, USB flash drives are mounted as empty CD-ROMs, and my wireless usb device still crashes the system. Also, with irqpoll enabled, I do eventually receive a "Disabling IRQ #16..." message, but this doesn't affect the usb devices that are already plugged in. Hope somebody has some idea!

---

### Post by mwaddoups on 2007-04-22
I finally fixed the problem! After being about to give up, and literally starting a download of another distro, I decided to have one last go. The boot options "acpi=noirq irqpoll" worked perfectly, and fixed this completely. Hope this helps anyone else with similar problems (which, judging from the amount of replies I received, is probably near zero!).

---

### Post by flipflopnick on 2007-08-04
thanx for your post, found it very useful. a linux guru friend gave me the acpi=noirq irqpoll in grub hint. this post confirmed it. I found if USB device plugged in at boot, sometimes they are recognised.

for others who read this, the solution is to add in[B] /boot/grub/menu.lst
[/B]
**acpi=noirq irqpoll**

after 

**root=UUID=69d794e4-50e1-4297-90e8-37df6acf6ae0 ro quiet splash **

to give 

[B]root=UUID=69d794e4-50e1-4297-90e8-37df6acf6ae0 ro quiet splash acpi=noirq irqpoll
[/B]
need to have root priviledges, so in terminal

**sudo gedit** and enter password

---

### Post by Tapatio01 on 2007-08-20
> **mwaddoups said:**
> I finally fixed the problem! After being about to give up, and literally starting a download of another distro, I decided to have one last go. The boot options "acpi=noirq irqpoll" worked perfectly, and fixed this completely. Hope this helps anyone else with similar problems (which, judging from the amount of replies I received, is probably near zero!).

I suspect that a lot of people are experiencing this problem. I would seem to have the same problem as you with USB devices (I have not yet tried your solution), and have seen a ton of discussion on this site and others regarding freeze-ups in Feisty, with lots of flailing around trying (with little success) to find some resolution. Because I am not constantly using USB devices, it was pretty easy to isolate this, because the freeze would take place only when using USB, and with every USB device that  I tried to use. Other people who are using USB mice, keyboards, networking, etc., are likely to see the symtoms as random.

I was confident it was not a hardware problem, as the same machine was rock-solid with Dapper and with Windows2000. Incidentally, I did have the same USB trouble when I briefly installed Debian Etch.

---

### Post by Tapatio01 on 2007-08-20
OK, making the edit to menu.lst didn't help. I have since found that it only affects devices plugged into my aftermarket PCI to USB adapter. Using the neglected USB 1.1 ports on the MoBo is no problem (except for slowness).

---

### Post by Barronmore on 2007-08-24
I've had this exact same problem on a Toshiba laptop and i've been having it sense Ubuntu 6.1.  I had actually given up on getting any linux to work on it but now that I've seen this I'll have to give it another shot.

I've traced my issue to the 3d acceleration drivers (both the official ATI and the Mesa).  For some reason anytime the 3d acclerations drivers are working inside a debian distro the USB just quits randomly.  The seem to work fine in any RPM distro I have tried, but I have installation degridation problems with ANY RPM distro I use.  So, I can't use USB in a Debian based distro and if I use RPM distros, they slowly stop working for me.  It's been a real pain.

I've never reported this because I've never fully understood how to discribe it.  But i'm willing to give it one more shot (and have to reinstall again!) to see if I can get it working.  Thanks

I'll let you all know how it goes.  But if there is a developer that can tell me why my 3d accleration keeps my USB devices in an RPM distro and not in a .deb distro I would greatly appriciate knowing why.

---

